# m114 Verschlüsselung

## Verschlüsselung/ Kryptografie  
Kryptografie ist die Wissenschaft der Verschlüsselung, Informationssicherheit und der Widerstandsfähigkeit gegen Manipulationen. Verschlüsselung und Entschlüsselung = encryption and decryption.

**Chiffre** Geheimcode/Algorithmus, der verwendet wird, um Daten zu verschlüsseln oder entschlüsseln.  
**Blockchiffre (block cipher)**   
Arbeiten mit festen Datenblöcken (64-168 Bit)  
Beispiele: DES, AES, IDEA  
Vorteile: Sicherer, robuster  

**Stromchiffre (stream cipher)**  
Verarbeiten Daten bit-/zeichenweise  
Beispiele: RC4, OFB, SEAL  
Vorteile: Echtzeitfähig  

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

Gleicher Schlüssel für Ver- und Entschlüsselung  
Vorteile: Schnell, einfach  
Nachteile: Schlüsselaustauschproblem  

**Cäsar-Verschlüsselung** (Rotationschiffre) jede lateinische Buchstaben des Alphabets wird **um N Stellen rotiert oder besser gesagt ersetzt**. Beispiel ROT-13, es verschieben sich Buchstaben um 13 nächsten Buchstaben. Cäsar Verschlüsselung ist monoalphabetischen Chiffrierverfahren, weil durch die selben Buchstaben ersetzt wird.  
Monoalphabetische Substitution  
Beispiel ROT-13: A → N, B → O  
Schwach: Häufigkeitsanalyse möglich  

Mit dem **CrypTool** zu **entschlüsseln**, Text eingeben. In den Tabs "Analyse/Symetrische Verschlüsselung (klassisch)/Cipher-Text Only/Caesar or whatever the algorithm is/Entschlüsseln where the Ermittelter Caesar-Schlüssel ist"

**Vigenere-Verschlüsselung** ist ein polyalphabetisches Chiffrierverfahren, weil ein Buchstaben wird mit verschiedenen Buchstaben chiffriert. Daher ist es auch schwieriger zu entschlüsseln als Cäsar.  
Ein Schlüssel, der meistens gleich lang wie der Klartext (plain understandable text) ist. Entschlüsseln mit einem Vigeneren-Quadrat, der Konzept, ist den Kreuzungspunkt zwei Buchstaben zu finden.
Der selbe Key/Schlüssel beim Absender und Empfänger.  
Polyalphabetische Substitution  
Verwendet Schlüsselwort  
Stärker als Cäsar, aber angreifbar  

**XOR-Stromchiffre** Exklusive-Oder-Verschlüsselung ist einfach und kann bei komplexeren Verfahren angewendet werden. Bit-für-bit ver-/entschlüsselt. Der Sender und Empfänger benutzen den selben Schlüssel in Form von binären Code. 
XOR: A 0 0 1 1 | B 0 1 0 1 | Y 0 1 1 0  
Sich das vertikal vorstellen. 00= 0, 11= 0, 01= 1, 10= 1  
Wichtig für moderne Kryptografie  
Schwach bei bekanntem Klartext  

**Hash-Wert Generierung**  
Einwegfunktion (irreversibel)  
Kollisionsresistenz  
Fester Ausgabewert (Fingerabdruck)  
**Arten von Hashing**:  
Algorithmus	Ausgabelänge Sicherheit  
MD5	128 bit	Unsicher  
SHA-1 160 bit Unsicher  
SHA-256	256 bit	Sicher  
SHA-3 variabel Sicher  


### Asymetrische Verschlüsselung

Schlüsselpaar: Public Key (veröffentlich) + Private Key (geheim)  
Vorteile: Kein Schlüsselaustauschproblem  
Nachteile: Langsamer, komplexer  

**RSA Verfahren**
RSA Schlüssellänge: 2048-4096 bit Anwendung: SSL/TLS, Email  
Wähle zwei Primzahlen p, q  
Berechne n = p*q  
Berechne φ(n) = (p-1)*(q-1)  
Wähle e mit ggT(e, φ(n)) = 1   
Berechne d mit e*d ≡ 1 mod φ(n)  
Public Key: (e,n), Private Key: (d,n)  

**Hybride Verfahren**
Kombination symmetrischer + asymmetrischer Verfahren  
Asymmetrisch für Schlüsselaustausch  
Symmetrisch für Datenverschlüsselung  

- TLS/SSL (HTTPS)
    - Asymmetrisch: RSA/ECC für Schlüsselaustausch
    - Symmetrisch: AES für Daten

- PGP/GPG (Email)
    - Asymmetrisch: RSA für Schlüssel
    - Symmetrisch: AES für Nachricht

**Signaturen und PKI (Public Key Infrastructure)**
Digitale Signaturen  
**1.** Sender erstellt Hash der Nachricht **2.** Verschlüsselt Hash mit Private Key **3.** Empfänger entschlüsselt mit Public Key **4.** Vergleicht mit eigenem Hash

PKI  
Zertifizierungsstellen (CA), X.509-Zertifikate, Vertrauensketten
