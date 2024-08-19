# Ciphers

Ciphers are algorithms used to encrypt or decrypt data. They transform plaintext into ciphertext (encryption) and vice versa (decryption) to ensure that only authorized parties can access the original information. Ciphers come in two main types:

1. Symmetric Ciphers: Use the same key for both encryption and decryption. This means both parties need to have the same secret key. Examples include AES (Advanced Encryption Standard) and DES (Data Encryption Standard).

2. Asymmetric Ciphers: Use a pair of keys—a public key and a private key. The public key is used for encryption, while the private key is used for decryption. Examples include RSA (Rivest-Shamir-Adleman) and ECC (Elliptic Curve Cryptography).

Ex: CIPHER, AES, DES, RC2

# PKI (Public Key Infrastructure)

PKI (Public Key Infrastructure) is a framework that manages digital certificates and public-key encryption. It supports the secure exchange of information by using public and private key pairs. PKI includes:

1. Certificates: Digital documents that associate a public key with the identity of the certificate holder. They are usually issued by a Certificate Authority (CA).

2. Certificate Authority (CA): An entity that issues digital certificates and verifies the identity of certificate holders.

3. Registration Authority (RA): Acts as a mediator between the user and the CA, handling requests for digital certificates.

4. Public and Private Keys: Used for encryption and decryption. The public key is shared openly, while the private key is kept secret.

PKI is fundamental for secure communications over networks, such as through SSL/TLS for HTTPS.

Ex: ED25519, RSA, RSA-KEM, X.509, PKCS#5, PKCS#7, PKCS#8, PKCS#10, PKCS#12,...

# Message Digest

A message digest is a fixed-size numeric representation of data derived from a larger piece of data using a hash function. Hash functions take input data (or "message") and produce a unique hash value (the digest) that acts as a fingerprint for that data. Key characteristics of hash functions include:

1. Deterministic: The same input will always produce the same digest.

2. Fixed Size: Regardless of the input size, the digest will always be the same length.

3. Fast Computation: Hash functions are designed to compute digests quickly.

4. Collision Resistant: It should be computationally infeasible to find two different inputs that produce the same digest.

Common hash functions include MD5, SHA-1, and SHA-256. Message digests are used for various purposes, including verifying data integrity and digital signatures.

Ẽx: SHA1, SHA256, SHA384, SHA512, MD5, HMAC
