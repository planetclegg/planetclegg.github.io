### Quick Reference Guide: Modern Cryptography

Cryptography is the science of securing information. Here’s a brief, practical overview of common cryptographic methods and their uses, without deep mathematics.

---

### 1. **Hashing (One-Way Cryptography)**
- **Purpose:** Verify data integrity and store sensitive data (e.g., passwords).
- **Characteristics:**
  - Transforms data into a fixed-length unique output ("hash").
  - Irreversible: You cannot reconstruct the original data from a hash.
  - Changing even one character produces a drastically different hash.
- **Use cases:** Password storage, file integrity checking, blockchain transactions.
- **Examples:** SHA-256, MD5 (now considered insecure).

---

### 2. **Symmetric Encryption (Shared-Key Cryptography)**
- **Purpose:** Encrypt and decrypt data quickly using a single shared key.
- **Characteristics:**
  - Same key used for both encryption and decryption.
  - Fast and efficient.
  - Challenge: Key management (sharing keys securely).
- **Use cases:** File encryption, disk encryption, secure network communication (VPN).
- **Examples:** AES (Advanced Encryption Standard).

---

### 3. **Asymmetric Encryption (Public-Key Cryptography)**
- **Purpose:** Securely encrypt data between two parties without sharing secret keys.
- **Characteristics:**
  - Uses a key pair: one public key (encrypt) and one private key (decrypt).
  - Slower than symmetric encryption; often used to securely exchange symmetric keys.
- **Use cases:** Secure email (PGP), HTTPS secure websites, secure messaging.
- **Examples:** RSA, ECC (Elliptic Curve Cryptography).

---

### 4. **Digital Signing (Authentication and Non-Repudiation)**
- **Purpose:** Prove the authenticity and integrity of data and verify the sender's identity.
- **Characteristics:**
  - Uses asymmetric cryptography but reversed: Sender signs data with their private key.
  - Anyone with the sender’s public key can verify the signature.
  - Confirms data has not been altered and identifies the signer.
- **Use cases:** Document signing, software updates, transaction authentication.
- **Examples:** Digital certificates, e-signature services, signed software packages.

---

### When to Use What?
- **Hashing:** Data integrity checks, storing passwords safely.
- **Symmetric Encryption:** Fast data encryption when parties already share a key.
- **Asymmetric Encryption:** Secure initial key exchange, secure communications between strangers.
- **Digital Signing:** Confirming authenticity, identity verification, and protecting data from tampering.

