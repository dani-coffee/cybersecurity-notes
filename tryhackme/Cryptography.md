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
1. **Secure key exchange** – safely share a symmetric key (used by WhatsApp, Signal, HTTPS)
2. **Digital signatures** – prove "this message really came from me"
   - Sign with private key → anyone verifies with my public key
  

---

Modern Encryption --> Hybrid 
1. Asymmetric (ECC/RSA) → securely exchange a random symmetric key. My device and the server swap a temporary AES key using ECC or RSA – this only happens once at the start  
2. Symmetric (AES or ChaCha20) → do the actual fast encryption of all messages/files usint the symmectirc key we obtained  from the asymmetric encryption --> After the key is safely shared, everything switches to AES or ChaCha20

Result:  
→ As safe as asymmetric  
→ As fast as symmetric




