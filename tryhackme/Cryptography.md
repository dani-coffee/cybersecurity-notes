# 🔑 **Types of encryption**

• `Symmetric Encryption` - uses **the same secret key** to both **encrypt** and **decrypt** data.

Popular Symmetric Algorithms:

| Algorithm | Used By                          | Notes                     |
|---------|----------------------------------|---------------------------|
| AES (Advanced Encryption Standard)   | WhatsApp, Wi-Fi, banks, disks    | The standard today       |
| ChaCha  | Google, Cloudflare, mobile apps  | Very fast on phones      |
| Salsa   | Modern protocols                 | Similar to ChaCha         |
|DES (Data Encryption Standard) |was used by banks and governments , nowadays none| DES was the world’s first official symmetric encryption standard,Completely broken since 1999|

### Advantages 
- Extremely fast
- Low battery/CPU usage
- Great for large files, live calls, full-disk encryption

### The One Big Challenge 
I must share the secret key securely with the other person.  
If an attacker steals the key → game over!

---


• `Asymmetric Encryption` -Asymmetric encryption (also called **public-key cryptography**) uses **two different keys**: a  Public Key used to **encrypt** or **verify** , and a Private Key used to **decrypt** or **sign**.
 if Alice wants to send somehting to Bob that only he can decrypt she woiuld use Bob's public key to send it.

Popular Asymmetric Algorithms:

| Algorithm  | Where You See It                            | Key Size (common) | Notes                              |
|------------|---------------------------------------------|-------------------|------------------------------------|
| RSA        | Old HTTPS sites, PGP emails                 | 2048 or 4096 bits | Still secure but slow              |
| ECC  (Elliptic Curve cryptography)      | Modern TLS, Bitcoin, iPhones                | 256–384 bits      | Same strength as RSA but much smaller & faster |
| Ed25519    | GitHub SSH keys, Signal, Wire              | 256-bit fixed     | Extremely fast and super secure    |

### Main Uses of Asymmetric Encryption
A. **Secure key exchange** (digital envelope,modern encryption)– safely share a symmetric key (used by WhatsApp, Signal, HTTPS): when two devices want to communicate securely, they need a shared symmetric key (for AES/ChaCha20).
But they must send this key in a way that attackers cannot steal it.

Asymmetric encryption solves this:
1. The server already has a public key and a private key ( symmetric)
2. My device creates a random symmetric key.
3. My device encrypts that symmetric key using the server’s public key.
4. Only the server can decrypt it using its private key.
5. Now both sides share the same symmetric key safely.
6. From this point on, all communication uses fast symmetric encryption.
Result:  
→ As safe as asymmetric  
→ As fast as symmetric


B. **Digital signatures** – prove "this message really came from me"
   - Sign with private key → anyone verifies with my public key
 

---

• `RSA` - RSA is the most widely used **public-key (asymmetric) encryption** algorithm.It lets two parties communicate securely without ever sharing a secret key beforehand.
RSA security relies on the fact that multiplying two large prime numbers is easy, but factoring the product back into the two original primes is **extremely hard**.

Key generation :

1. Choose two large random prime numbers `p` and `q` (e.g. 2048 bits each today)  
2. Compute `n = p × q` → this is part of the public key  
3. Compute ` ϕ(n) = n − p − q + 1 `
4. Choose `e` (usually 65537) such that 1 < e < λ(n) and gcd(e, λ(n)) = 1  
5. Compute `d` such that `d × e ≡ 1 (mod λ(n))` → this is the private key  

Public key = (n, e)  
Private key = (n, d)  or just d (since n is public)

---

• `Diffie-Hellman Key Exchange` - Diffie-Hellman is a way for two people to share a secret key over the internet, without ever sending the secret key itself.
Publicly agreed values (everyone knows these):
- A big prime number `p`
- A base `g` (usually a small number like 3 or 5)

Steps:
1. Alice picks secret number `a`  
   Bob picks secret number `b`

2. Alice computes `A = g^a mod p` → sends A to Bob (public)  
   Bob computes `B = g^b mod p` → sends B to Alice (public)

3. Alice computes `B^a mod p` = `(g^b)^a mod p` = `g^(b×a) mod p`  
   Bob computes `A^b mod p` = `(g^a)^b mod p` = `g^(a×b) mod p`

Because `a×b = b×a`, both get the **exact same number** → this is their shared secret.
Third party/uninvited guest sees only `g`, `p`, `A`, and `B` — they would need to solve the **Discrete Logarithm Problem** to find `a` or `b`. That’s believed to be very hard (similar security level to RSA factoring).


---

# 🔧 **Tools**

• `ssh-keygen` - ssh-keygen is the tool used to generate SSH key pairs.

Common SSH Key Algorithms

DSA
Older digital-signature algorithm. Mostly outdated.

ECDSA
Uses elliptic-curve cryptography. Smaller keys with similar security.

ECDSA-SK
ECDSA but stored on a hardware security key (e.g., YubiKey).

Ed25519
Modern, fast, and secure. Recommended for most users.

Ed25519-SK
Ed25519 protected by a hardware security key.

RSA
Classic and widely supported. Still common, but keys must be large (2048–4096 bits).

---

• `John the Ripper` - A popular password-cracking tool used to test password strength or recover lost passwords. It can crack hashes, encrypted files, and more.

---

• `Hashcat` - password cracking tool used in penetration testing to test the strength of hashed passwords using wordlists or brute-force techniques.syntax: hashcat -m <hash_type> -a <attack_mode> hashfile wordlist. Example: hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt ( where -m 3200 is for bcrypt, -m 1800 for sha512 and -m 1400 for sha256 and -a 0 is for dictionary attack)

---

| Command | Example | Description |
|---------|---------|-------------|
| `ssh-keygen` | `ssh-keygen -t ed25519 -C "mykey"` | Tool used to **generate SSH key pairs** (private and public keys). |
| `ssh -i <privateKeyFile> user@host` | `ssh -i ~/.ssh/id_rsa thm@10.10.200.25` | Connects to a server using your **private key** instead of a password. Replace `<privateKeyFile>` with your key, `user` with the server username, and `host` with the server IP or domain. |
| `authorized_keys` | `cat ~/.ssh/authorized_keys` | File on the server that lists **public keys allowed to log in**. You can view it with `cat` or edit it to add a key. |
|  `gpg --import backup.key` | `gpg --import backup.key` | Import a backup GPG private key to a new computer. |
| `gpg --decrypt confidential_message.gpg` | `gpg --decrypt confidential_message.gpg` | Decrypt messages using your imported GPG key. |
|  `hexdump <file>` | `hexdump file1.txt` | Displays the file contents in hexadecimal only (grouped words). Does not show ASCII characters. |
|  `hexdump -C <file>` | `hexdump -C file1.txt` | Shows file contents in canonical format: hex bytes on the left and ASCII representation on the right. |
|  `hexdump -c <file>` | `hexdump -c file1.txt` | Prints character (ASCII) values of each byte instead of hex — useful for inspecting ASCII only. |
|`md5sum <file>`	| md5sum file.txt	| Calculates the MD5 hash of the file. Useful for verifying file integrity, but not secure for cryptographic purposes.|
|`sha1sum <file>`	|sha1sum file.txt	Calculates the SHA-1 hash of the file. Stronger than MD5, but still considered insecure for modern cryptography.|
|`sha256sum <file>`	|sha256sum file.txt	| Calculates the SHA-256 hash of the file — widely used and considered secure for integrity and cryptographic validation.|
|`sha512sum <file>`	|sha512sum file.txt	| Calculates the SHA-512 hash of the file — similar to SHA-256 but with a longer, more computation-heavy hash for high-security environments.|
|`sha512sum <file>`	|sha512sum file.txt	| Calculates the SHA-512 hash of the file — similar to SHA-256 but with a longer, more computation-heavy hash for high-security environments.|
| `head -n 20 <filename>` | `head -n 20 rockyou.txt` | Displays the first 20 lines of a file (useful for previewing wordlists like rockyou.txt). |


# 🧠 **Additional notes**

• On Linux, password hashes are stored in /etc/shadow.The encrypted password field stores the password in hashed form and has four parts:$prefix$options$salt$hash
 1. Prefix – shows which hashing algorithm was used.
 2. Options – parameters for the hash (like cost or memory settings).
 3. Salt – a random value added to the password before hashing.
 4. Hash – the actual result of hashing the password + salt.

•Windows passwords use NTLM (based on MD4) and are stored in the SAM database(usually located at  C:\Windows\System32\config\SAM). NTLM hashes look like MD4/MD5, so context helps identify them. Windows also keeps old LM hashes for compatibility. Tools like Mimikatz can extract these hashes. To recognize a hash, check its length, encoding, or source. For reference, [Hashcat Example Hashes](https://hashcat.net/wiki/doku.php?id=example_hashes)

• `Salt` - A salt is just a random string added to your password before hashing.It makes every hash unique, even if two people use the same password.

• `Pepper` - Pepper is a hidden secret added to passwords before hashing, stored outside the database, so even if attackers steal all hashes and salts, they still can’t crack passwords without guessing the pepper too.

• `rainbow table` -  A huge precomputed dictionary of hash → password mappings that only works when hashes are unsalted.

•` Hash vs HMAC` -  SHA256 is a hashing algorithm used to ensure data integrity. HMAC is also a hashing method, but it includes a secret key to provide authentication. Neither SHA256 nor HMAC are encryption or encoding, and their outputs cannot be reversed.


