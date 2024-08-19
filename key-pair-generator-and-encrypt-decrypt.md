# OpenSSL Key Pair Generation and Message Encryption/Decryption Guide

**Introduction**

This guide details the steps to generate an RSA key pair, and then use these keys to encrypt and decrypt a message using OpenSSL. This guide is based on OpenSSL 3.0 and later, where the rsautl command has been deprecated in favor of pkeyutl.

**Prerequisites**

OpenSSL 3.0 or later installed on your Linux system.

1. Generating RSA Key Pair

   1.1 Generate an RSA Private Key
   Generate a private key encrypted with a passphrase:

`openssl genpkey -algorithm RSA -out private_key.pem -aes256`

- algorithm RSA: Specifies RSA as the encryption algorithm.

- out private_key.pem: Specifies the filename for the private key.

- aes256: Encrypts the private key using AES-256.

- passphrase: `kris`

  1.2 Extract the Public Key
  Extract the public key from the private key:

`openssl rsa -pubout -in private_key.pem -out public_key.pem`

- pubout: Indicates that the output will be the public key.
- in private_key.pem: Specifies the private key file to extract the public key from.
- out public_key.pem: Specifies the filename for the public key.

2. Encrypting a Message Using the Public Key

   2.1 Create a File with the Message

   Create a file containing the message to be encrypted:

```
echo "hello world" > message.txt
```

    2.2 Encrypt the Message

    Encrypt the message using the public key:

`openssl pkeyutl -encrypt -inkey public_key.pem -pubin -in message.txt -out message.enc`

- encrypt: Specifies the operation as encryption.
- inkey public_key.pem: Specifies the public key file to use for encryption.
- pubin: Indicates that the key is a public key.
- in message.txt: Specifies the input file containing the plaintext message.
- out message.enc: Specifies the output file for the encrypted message.

3. Decrypting the Message Using the Private Key
   3.1 Decrypt the Message
   Decrypt the encrypted message using the private key:

`openssl pkeyutl -decrypt -inkey private_key.pem -in message.enc -out message_dec.txt`

- decrypt: Specifies the operation as decryption.
- inkey private_key.pem: Specifies the private key file to use for decryption.
- in message.enc: Specifies the input file containing the encrypted message.
- out message_dec.txt: Specifies the output file for the decrypted message.
  3.2 Verify the Decryption
  Check the contents of the decrypted message:

`cat message_dec.txt`
You should see:

`hello world`

Notes

- Padding and Algorithms: By default, pkeyutl uses PKCS#1 v1.5 padding for RSA encryption. For other padding schemes or options, consult the OpenSSL documentation or use additional flags.
- Message Size: RSA encryption has size limitations due to padding and key size. For larger messages, consider hybrid encryption where a symmetric key (e.g., AES) encrypts the data and the symmetric key is encrypted with RSA.
- In the real project, it's generally recommended to encode the encrypted message content to `Base64` when dealing with binary data. This is because encrypted data is typically in binary format, and many text-based systems or protocols (like email or certain storage systems) handle text data better than binary data. Base64 encoding converts binary data into ASCII text, making it easier to handle in these contexts.

  **Conclusion**

  This guide provides a step-by-step process for generating RSA keys, encrypting a message with a public key, and decrypting it with a private key using OpenSSL 3.0. For further customization and advanced usage, refer to the OpenSSL documentation.
