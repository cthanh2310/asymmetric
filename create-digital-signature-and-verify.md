# creating a digital signature of a message with a private key and then verifying that signature with the corresponding public key

1. Sign a Message

   1.1 Create the Message File

First, create a file containing the message you want to sign:

```
echo "hello world" > message.txt

```

1.2 Sign the Message

Use the `openssl dgst` command to create a signature of the message. Here, we'll use the SHA-256 hashing algorithm and sign it with the private key:

```
openssl dgst -sha256 -sign private_key.pem -out message.sig message.txt
```

- `sha256`: Specifies the hashing algorithm (SHA-256).
- `sign private_key.pem`: Specifies the private key to use for signing.
- `out message.sig`: Specifies the file to output the signature.
- `message.txt`: The file containing the message to be signed.

2. Verify the Signature

   2.1 Verify the signature
   To verify the signature using the public key, use the following command:

```
openssl dgst -sha256 -verify public_key.pem -signature message.sig message.txt
```

- sha256: Specifies the hashing algorithm used to sign the message.
- verify public_key.pem: Specifies the public key to use for verification.
- signature message.sig: Specifies the file containing the signature.
- message.txt: The file containing the original message.

If the signature is valid, OpenSSL will output:

```
Verified OK
```

Vice versa, OpenSSL will output:

```
Verification Failure
```

Reference: https://docs.openssl.org/master/man1/openssl-pkeyutl/#notes
