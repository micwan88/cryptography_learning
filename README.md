# cryptography_learning
This is a repo to put stuffs related to cryptography learning

## Stuffs related to RSA/PKCS/SPKI
- utils/pkcs_spki_reader.html: webpage to parsing pkcs/spki from DER bytes in HEX (by ChatGPT)
- utils/rsa_keypair_verification.html: webpage to verify if public and private key are in pair or not (by ChatGPT)

## Notes about PKCS/SPKI/ASN.1/DER/PEM (By ChatGPT)
1. ASN.1 - The language used to define structures.

        RSAPrivateKey ::= SEQUENCE {
            version           INTEGER,
            modulus           INTEGER,  -- n
            publicExponent    INTEGER,  -- e
            privateExponent   INTEGER,  -- d
            ...
        }

2. DER - The binary encoding of ASN.1 objects.
    Every ASN.1 structure can be serialized to DER. DER is what computers actually store/transmit.

3. PEM - Just Base64 encoding of DER with ASCII headers
    Human-friendly, copy/paste-friendly. Example: PKCS#8 private key in PEM is literally DER → Base64 → wrapped with headers.

4. PKCS#1 / PKCS#8 / SPKI - These are specific ASN.1 structures (standards) for keys:

    PKCS#1: RSA keys only.

        Public key: (n, e)
        Private key: (n, e, d, p, q, dp, dq, qi)

    PKCS#8: Generic private key container.

        Algorithm identifier (RSA, EC, etc.)
        Private key bytes (for RSA, that’s usually a PKCS#1 structure inside).

    SPKI (SubjectPublicKeyInfo): Generic public key container.
    
        Algorithm identifier
        Public key bytes (for RSA, that’s usually (n, e) like PKCS#1 public).