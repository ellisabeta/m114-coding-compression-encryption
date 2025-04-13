# m114 Verschlüsselung

## Verschlüsselung/ Kryptografie  
Kryptografie ist die Wissenschaft der Verschlüsselung, Informationssicherheit und der Widerstandsfähigkeit gegen Manipulationen. Verschlüsselung und Entschlüsselung = encryption and decryption.

**Chiffre** Geheimcode/Algorithmus, der verwendet wird, um Daten zu verschlüsseln oder entschlüsseln.  
**Blockchiffre (block cipher)** wird in Blöcken unterteilt. Schlüssellänge 64, 112, 128, 168 Bit. Es verschlüsselt den Schlüsselwert miteinander in ganzen Datenblöcken. Blockchiffre sind robuster und sicherer als Stromchiffre. **DES, AES, IDEA**  
**Stromchiffre (stream cipher)** entschlüsselt Nachrichten Bit für Bit bzw. Zeichen für Zeichen. Für Echtzeitübertragungen dafür da. **RC4, OFB, SEAL, A5/1**  

- AES= is a symmetric block cipher. Symmetric-key algorithm meaning the same key is used for both encrypting and decrypting the data. (Advanced Encryption Standard)
- DES= is a symmetric-key block cipher algorithm similar to AES just smaller, which uses a key of 56-bit size. (Data Encryption Standard)
- IDEA= is a symmetric key block cipher encryption. IDEA uses a 128-bit key and operates on 64-bit blocks. (International Data Encryption Algorithm)
- RC4= is a stream cipher, it uses either 64 bit or 128-bit key sizes. (Rivest Cipher 4)
- XOR= cipher is an additive cipher, it combies plaintext with a secret key using the XOR, resulting in encrypted data that can only be decrypted using the same key. (Exclusive Or)
- RSA= is a public-key cryptosystem to encrypt and a private key to decrypt. (Rivest, Shamir, Adleman) 
- ECC using public and private keys for decryption and encryption (Elliptic Curve Cryptography)
- SHA creates a hash to encrypt data. Usually uses algorithms TLS, SSL, PGP, SSH etc. (Secure Hash Algorithms)  

Mit dem selben Schlüssel verschlüsseln und entschlüsseln heisst Symetrische Verschlüsselungsverfahren.  

### Symetrische Verschlüsselungen

**Cäsar-Verschlüsselung** (Rotationschiffre) jede lateinische Buchstaben des Alphabets wird **um N Stellen rotiert oder besser gesagt ersetzt**. Beispiel ROT-13, es verschieben sich Buchstaben um 13 nächsten Buchstaben. Cäsar Verschlüsselung ist monoalphabetischen Chiffrierverfahren, weil durch die selben Buchstaben ersetzt wird.

Mit dem **CrypTool** zu **entschlüsseln**, Text eingeben. In den Tabs "Analyse/Symetrische Verschlüsselung (klassisch)/Cipher-Text Only/Caesar or whatever the algorithm is/Entschlüsseln where the Ermittelter Caesar-Schlüssel ist"

**Vigenere-Verschlüsselung** ist ein polyalphabetisches Chiffrierverfahren, weil ein Buchstaben wird mit verschiedenen Buchstaben chiffriert. Daher ist es auch schwieriger zu entschlüsseln als Cäsar.  
Ein Schlüssel, der meistens gleich lang wie der Klartext (plain understandable text) ist. Entschlüsseln mit einem Vigeneren-Quadrat, der Konzept, ist den Kreuzungspunkt zwei Buchstaben zu finden.
Der selbe Key/Schlüssel beim Absender und Empfänger.

**XOR-Stromchiffre** Exklusive-Oder-Verschlüsselung ist einfach und kann bei komplexeren Verfahren angewendet werden. Bit-für-bit ver-/entschlüsselt. Der Sender und Empfänger benutzen den selben Schlüssel in Form von binären Code. 
XOR: A 0 0 1 1 | B 0 1 0 1 | Y 0 1 1 0  
Sich das vertikal vorstellen. 00= 0, 11= 0, 01= 1, 10= 1  

### Asymetrische Verschlüsselung

**RSA Verfahren**

**Hybride Verfahren**
