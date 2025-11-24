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


• `Asymmetric Encryption` -Asymmetric encryption (also called **public-key cryptography**) uses **two different keys**: a  Public Key used to **encrypt** or **verify** , and a Private Key used to **decrypt** or **sign**
Popular Asymmetric Algorithms:

| Algorithm  | Where You See It                            | Key Size (common) | Notes                              |
|------------|---------------------------------------------|-------------------|------------------------------------|
| RSA        | Old HTTPS sites, PGP emails                 | 2048 or 4096 bits | Still secure but slow              |
| ECC  (Elliptic Curve cryptography)      | Modern TLS, Bitcoin, iPhones                | 256–384 bits      | Same strength as RSA but much smaller & faster |
| Ed25519    | GitHub SSH keys, Signal, Wire              | 256-bit fixed     | Extremely fast and super secure    |

### Main Uses of Asymmetric Encryption
1. **Secure key exchange** – safely share a symmetric key (used by WhatsApp, Signal, HTTPS) - Encrypt with the public key → decrypt with private key 
2. **Digital signatures** – prove "this message really came from me"
   - Sign with private key → anyone verifies with my public key
  

---

Modern Encryption --> Hybrid 
1. Asymmetric (ECC/RSA) → securely exchange a random symmetric key. My device and the server swap a temporary AES key using ECC or RSA – this only happens once at the start  
2. Symmetric (AES or ChaCha20) → do the actual fast encryption of all messages/files usint the symmectirc key we obtained  from the asymmetric encryption --> After the key is safely shared, everything switches to AES or ChaCha20

Result:  
→ As safe as asymmetric  
→ As fast as symmetric



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




| Command | Example | Description |
|---------|---------|-------------|
| `ssh-keygen` | `ssh-keygen -t ed25519 -C "mykey"` | Tool used to **generate SSH key pairs** (private and public keys). |
| `ssh -i <privateKeyFile> user@host` | `ssh -i ~/.ssh/id_rsa thm@10.10.200.25` | Connects to a server using your **private key** instead of a password. Replace `<privateKeyFile>` with your key, `user` with the server username, and `host` with the server IP or domain. |
| `authorized_keys` | `cat ~/.ssh/authorized_keys` | File on the server that lists **public keys allowed to log in**. You can view it with `cat` or edit it to add a key. |
|  `gpg --import backup.key` | `gpg --import backup.key` | Import a backup GPG private key to a new computer. |
| `gpg --decrypt confidential_message.gpg` | `gpg --decrypt confidential_message.gpg` | Decrypt messages using your imported GPG key. |
