## A Brief Introduction to Cryptography

This guide aims to show how cryptography evolved over time, focusing on the difference between **symmetric** and **asymmetric** (public-key) encryption, how they’re used together, and where hashing fits into the picture. Comments labeled **JEC:** are my notes

---

### 1. Basic Terminology

- **Cipher (Cypher)** – An algorithm or set of instructions that describes how to transform readable text (plaintext) into unintelligible text (ciphertext), and in some cases, how to transform it back.  
- **Plaintext** – The original, readable message or data.  
- **Ciphertext** – Encrypted text that is not meant to be readable without decryption.

---

### 2. Cryptography’s Core Goal

Cryptography is about sending information over potentially insecure channels without unwanted parties reading or altering it. Historically, if a messenger on horseback was intercepted, unencrypted messages would be exposed. Encryption prevents that.

---

### 3. Symmetric Key Cryptography (Shared Key)

- **Concept:** Uses the **same secret key** to encrypt and decrypt.  
- **Examples (Historical to Modern):**  
  - Ancient: Caesar cipher, Vigenère cipher  
  - WW2: Enigma machine  
  - Modern: AES (Advanced Encryption Standard, also known as Rijndael), DES (now outdated), 3DES, Blowfish  
- **Advantages:**  
  - Fast, computationally efficient  
  - Suitable for bulk data encryption  
- **Challenges:** Key distribution. Both sender and recipient must share the same key and keep it secret.

**Key Sharing Problem**  
Before the 1970s, the only known approach was to physically (or otherwise securely) deliver the key to the intended recipient. 
**JEC note:** This required trusted couriers, elaborate secrecy protocols, etc.

---

### 4. Asymmetric Key Cryptography (Public-Key)

- **Concept:** Each participant generates a pair of keys: a **private key** (secret) and a **public key** (freely shared).
- The two keys are mathematically related but knowledge of the public key does **not** typically reveal the private key.  
- **Encryption and Decryption:**  
  - To send a secret message to someone, you use **their** public key to encrypt.  
  - They use their matching **private key** to decrypt.
  - JEC: To send messages back and forth, each party uses their own private keys to decrypt and the others public key to encrypt.
- **Digital Signatures:**  
  - A sender can use their private key to “sign” a document.  
  - Anyone with the sender’s public key can verify it was indeed signed by that private key.
  - See below for detail
- **Key Players:**  
  - Whitfield Diffie and Martin Hellman pioneered public-key techniques in the 1970s.  
- **Impact:** Solved the key distribution problem for symmetric encryption by letting users share secrets over insecure channels.

---

### 5. Hybrid Approach (Using Both)

Most modern secure communication protocols (e.g., **TLS** for HTTPS) combine **asymmetric** and **symmetric** cryptography:
1. **Asymmetric** methods securely exchange a new symmetric key.
2. **Symmetric** methods then encrypt the main data stream for efficiency.

**JEC note:** This solves the classic problem of sharing a secret key without couriers, while retaining the speed advantages of symmetric encryption.
**JEC note:** HTTPS used to use SSL, this was later replaced with TLS due to weakenesses found in SSL. There were multiple versions of TLS up to 1.3 which is generally used now.

---

### 6. Encryption vs. Hashing

Although both belong under the “cryptography” umbrella, **encryption** and **hashing** serve different purposes:

- **Encryption** – Ensures confidentiality of data (makes it unreadable to unauthorized parties but recoverable by authorized parties).  
- **Hashing** – Transforms data into a fixed-size “digest” used primarily for verifying integrity. A hash cannot be reversed to recover the original content; it’s useful for checksums, password storage, and data integrity.

---

### 7. Putting It All Together

- **Symmetric Encryption:** Fast and efficient for everyday data encryption, but needs a secure way to share the key.  
- **Asymmetric Encryption:** Enables secure key exchange over insecure channels and digital signatures.  
- **Hashing:** Checks data integrity or stores sensitive information (passwords) in a non-reversible form.

Combining these cryptographic tools gives us the foundations of modern secure communication—whether it’s two generals planning strategy, or your browser securely connecting to an online store.
---

# More explanations on sometimes confusing parts:

**Digital Signatures with Hashing**  
When a sender signs a document, they usually don’t sign the entire document directly. Instead, they do the following:

1. **Hash the Document:** The sender runs the document through a cryptographic hash function (like SHA-256), which produces a fixed-size digest (a unique “fingerprint” of the document).  
2. **Sign the Hash:** The sender then uses their **private key** to encrypt or sign that hash, creating a unique digital signature.  
3. **Verify the Signature:**  
   - A receiver takes the original document, hashes it, and compares the hash to what’s revealed when they use the sender’s **public key** to decrypt or verify the signature.  
   - If the hashes match, it proves two things:  
     - **Authenticity:** Only someone with the private key could have produced that signature.  
     - **Integrity:** The document hasn’t been altered; any change would produce a different hash, invalidating the signature.

## more background on hashing
this is me manually using "shasum" a commandline utility for generating SHA hashes on my computer.
file1.txt contains the text "this is a file.", file2.txt contains the text "This is a file." 
note that the length of the file is identical and the only thing that is different is the second file starts with a capital "T"
```bash
$ # first we'll use a sha1 hash to demonstrate.  the long numbers are in hex so they contain 0-9 and A-F

$ shasum5.34 -a 1 file1.txt 
b78087338d3daf51e667056c78fd8089bb51d5ec  file1.txt
$ shasum5.34 -a 1 file2.txt 
d7dff2b1ef48b9c20c23d7b3a08b557957cec3c9  file2.txt

$ # now i'll hash the same files with SHA-256.  Notice the hash number is different
$ shasum5.34 -a 256 file1.txt 
590c9fa5b7b3d66f1bf274080fd6c6fd781357c44a255f6f14f77bcba0585fc5  file1.txt
$ shasum5.34 -a 256 file2.txt 
f02d5a72cd2d57fa802840a76b44c6c6920a8b8e6b90b20e26c03876275069e0  file2.txt

$ # Notice that the tiniest change to the file generated a radically different hash.

#outputing the file contents
$ cat file1.txt 
this is a file.
bash-3.2$ cat file2.txt 
This is a file.
```

Any size file can be hashed this way, the length of the hashes are always the same for each hashing algorithm 
(regardless of the size of the file being hashed), and are specified by the algorithm itself:

- SHA-1 generates 160 bit hashes
- SHA-256 generates 256 bit hashes
- SHA-512 generates 512 bit hashes

Larger sized hashes are generally better than smaller ones, but for large inputs take longer to generate.
SHA-1 replaced MD5, which was found to have a vulnerability
SHA-256 has generally replaced SHA-1, and will probably be superseded by something else eventually.

what makes a hashing algorithm a "cryptographically secure hashing algorithm" (aka Secure Hash Algorithm) is that it is considered *very* 
difficult to easily produce a "hash collision".  A collision is where you find two files that are different, but still produce the same hash.
if an attacker could do generate hash collisions easily, it breaks things like signing.  how resistant a hashing algorithm is to collision attacks
is partly the output length (longer the better), and partly the internal algorithm of how it munges all the bits together from a file to produce the hash.

