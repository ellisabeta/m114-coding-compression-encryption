# m114

## Datenspeicher und Datenübertragung
Digital gespeicherte Daten, die übertragen werden, sind in der Form von **Bit**.
Bit ist entweder 1 oder 0.

- Byte &rarr; 8 bits
- WORD &rarr; 16 Bits
- DWORD &rarr; 32 Bits 
- QWORD &rarr; 64 Bits   
Dadurch ist die Anzahl Bit-Kombinationen ausrechenbar.

**Byte** Grosse B steht für Byte (100M**B**). Ein Byte entpricht zwei Hex-Ziffern. 1 Byte = 256 Bitkombinationen.  
**Bitkombinationen** Formel: **Anzahl Bit-Kombinationen = 2^Anzahl Bitstellen** (bitstellen sind wie viele Bits es sind) Beispiel 2^16 (16 sind eben bits) = 65'536 Kombinationen.  
Umgekehrt **Anzahl Bit** Formel: **Anzahl Bit = round it up(Log"Bit Kombination" / log2)** Kontrolle: **2^Anzahl Bit**  
**Zahlenkreis** 
Der Speicher hat bis zu 255 Byte Platz (= 1111 1111). Wenn es zu über 255 Byte kommt, kommt es zu einem Datenüberlauf. Daher bei 256 +1 Byte wächselt es zu 0 und ist beim Zahlenkreis wieder am Anfang. 

**Signed and Unsigned**   
By default ist alles positiv definiert  
&rarr; unsigned = positive Zahlen 0-255  
&rarr; signed = positive und negative Zahlen -128-127 weil das erste Zeichen der Vorzeihen (-/+) ist.  
unsigned overflow = binär ebene  
signed overflow = dezimal ebene    
n= Bit stellen
*Signed Formel*: (min) -2^(n-1), (max) 2^(n-1)-1
*Unsigned Formel*: (min) 0, (max) 2^n -1   

**MSB**: most significant bit = höchswertige Bit entweder 255 oder 127
**LSB**: least significant bit = niedrigstwertiges Bit entweder 0 oder -128

**Zahlensystem** bin &rarr; dez = (dez num)v10 = (binary number * 2^position of binary number) + (bv1 * 2^1) + (bv2 * 2^2)... so for 1011 it will be 1*2^3 + 0*2^2 + 1*2^1 + 1*2^0 = 8+0+2+1= 11  
dez &rarr; bin = the whole dez/2 rest is the binary numbers  | dez &rarr; hex = full dez num/16 devide each result until the rest is smaller than what youve been deviding by. Reverse Remainders und wandle um ins bin oder hex.  
bin &rarr; hex = from lsb add up the bin stellen zusammen 0111 = 0 4 2 1 = 7  
hex &rarr; dez = (n*16^3) + (n*16^2) + (n*16^1) + (n*16^0) potenz 0 gibt immer 1  
for hex to bin convert it first to dez.

## Codesysteme
Es hat vier Arten von Codes: Numerische (alles in Binärischen Codes dargestellt), Alphanumerische (Zeichen in Bitfolgen darzustellen), Strich-code (Code auf verpackungen) etc. Code muss Umgekehrabbildung nach der Umwandlung/Verarbeitung zurück geben.  

**Gleitkommazahlen** Gleitkommaformat ist in IEEE-754 Format. Vorzeichen, Exponent, Mantisse. Vorzeichen (-/+), Exponent 8 Bit lang, Mantisse 23 Zeichen. Exponent = signed, Exponent bias ist immer 127, weil es signed ist. Mantisse = unsigned (immer positiv).
  
**Alphanumerische Code** Dient dazu da um Text zu codieren.  
&rarr; ASCII-Code: 7 Bit-Zeichenkodierung welches 128 Zeichen darstellen kann (American Standard Code for Information Interchange) umfassen das lateinische Alphabet, Sonderzeichen usw.  
&rarr; Steuerzeichen (control characters) die wichtigsten zu merken sind: 08h= BS backspace, 09h= HT horizontal tab, 0Ah= LF line feed, 0Dh= CR carriage return, 1Bh= ESC escape, 20h= SP space, 30h= 0, 41h= A, 61h= a  
&rarr; ISO-8859 and ANSI Code: ISO-8859 braucht 8 Bits und kann 255 Zeichen darstellen, doppelt so viel wie ASCII. Es hat verschiedene versionen von ISO für alle verschiedene Sprachen.  
&rarr; Unicode UTF-8: Unicode kann maximal **4 Byte** lang sein. Verschiedene Zeichen im Bereich von U+00000000 bis U+FFFFFFFF. Unicode ist für alle denkbaren Zeichen dafür da. UTF-8 belegt pro Zeichen 1,2,3 oder 4 Byte. UTF-8 weniger speicheraufwendig. UTF-32 with 4 Bytes, UTF-16 2 or 4 Bytes, UTF-8 1-4 Bytes

UTF-8 uses some more complex characters. To know which character is not as simple as the ASCII characters we should look at the binary.  

**Vier UTF-8 Zeichen codes**: erster Byte ist ein Start-Byte in UTF-8. Fängt start-byte mit 0 one-byte Zeichen ist es ein einfaches ASCII Zeichen. Fängt es mit 110 two-byte Zeichen, 1110 three-byte Zeichen, 11110 four-byte Zeichen ist es ein Multi-byte Zeichen. 

**Byte-Reihenfolge LE, BE** BE= Big-Endian, wird nach dem höchstwertigen Byte zuerst gespeichert. LE= Little-Endian, wird nach dem kleinstwertigsten Byte gespeichert. UTF-8-LE-BOM (das heisst nach dem kleinsten Byte gespeichert)

**EAN-Code** schwarz weisse Balken Code, 8-stellige oder 13-stellige Zahl. Letzte Zahle ist die Prüfziffer.  
**EAN-8** Jede von den 8 Zahlen oder Zeichen besteht aus 7 gleich grossen Spalten (schwarz=1 weiss=0). Randzeichen 101 und Trennzeichen 01010. Die prüfziffer ist immer die letze.  
**QR-Code** Verlust von 7% der Daten auf dem QR-Code (verschmutzt oder was anderes) führt zu Fehlerkorrektur-Level L. Bei 30% Beschädigung ist es Fehlerkorrektur-Level H.

## Bildcodierung
PPI = pixel per inch  
DPI = dots per inch &rarr; beim Vierfarbendruck  
px= Pixel aus rot, blau, grünen Farbpunkten /
dot = bei Druckverfahren ein Farbpunkt entsteht Rastermuster mit verschiedenen Grössen und Anordungen.

**Farbräume** Farbe als Koordinatensystem oder mathematisches Modell dargestellt
Die 4 Farbräume sind:
- RGB (red, green, blue)
- CMYK (cyan, magenta, yellow, keycolor=black)
- HSL (hue=farbton, saturation=intensität, lightness)
- YUV (luminanz Y, chrominanz V,U)  
#FF0000 red, #00FF00 green, #0000FF blue, #FFFF00 yellow, #00FFFF cyan, #FF00FF pink, #000000 black, #FFFFFF white, #808080 grey

**Vektorgrafik** bestehen aus Linien, Kreisen und Kurven, die verlustfrei skaliert werden können (beliebig vergrössert werden) im Gegensatz zu Rastergrafiken. Oft für Fonts verwendet bei Bildschirmen oder Druckern.

**Alphakanal Transparenz** Alphakanal bedeutet Durchsichtigkeit der einzelnen Pixel. Dazu wird ein zusätzlichen Byte verwendet.  
Formate, die Alphakanal unterstützen: TIFF, TGA, PNG, PSD, GIF.

-------------------------------------------------------------------------------------------

unsigned: 1111 0000 = 1*2^7 + 1*2^6 + 1*2^5 + 1*2^4 + 0*2^3 + 0*2^2 + 0*2^1 = 240  
signed: 1111 0000 = -1*2^6 + -1*2^5 + -1*2^4 + 0*2^3 + 0*2^2 + 0*2^1 = -112  
-1*2^7 + 1*2^6 + 1*2^5 + 1*2^4

**signed: 0 = 0*2^7 + Rest welche auf 1 gesetzt sind | 1 = -1*2^7 + Rest welche auf 1 gesetzt sind**

TASK FROM ORIOL:
alles signed
0000 0000 = 0
1000 0000 = -1*2^7 = -128
1111 1111 = -1*2^7 + 2^6 + 2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0 = -1
1010 1010 = -1*2^7 + 0 + 2^5 + 0 + 2^3 + 0 + 2^1 + 0 = -86
0101 0001 = 0 + 2^6 + 0 + 2^4 + 0 + 0 + 0 + 2^0 = 81
1101 0110 = -1*2^7 + 2^6 + 0 + 2^4 + 0 + 2^2 + 2^1 + 0 = -42

Gleitkommazahl
Zahl 2.0 in IEEE 754 Single Precision darstellen

Vorzeichen 0
Vorkommazahl = 10
Nachkommazahl = 0

Zusammengesetzt = 10.0 * 2^0 -> 1.00*2^1
Exponent = 127 + 1 = 128 = 1000 0000
Mantisse = 23 Mal eine 0

0 1000 0000 23MAl 0

------------------------------------------------------------------------------------------

## Kompression
Kompressionsverfahren vor allem bei Bildern, ist wenn der urpsrüngliche Daten reduziert werden. Meistens um redundante Informationen zu entfernen. Umgekehrter Prozess ist Dekompression (Dekomprimierung).  
Verlustfreie Komprimierung, ist wenn alle Originaldaten zurück gewonnen werden können. Komprimierung = weniger Platz.

**Kompressionsrate K** = (Originalgrösse - Komprimierte Grösse) / OriginalGrösse  
**Kompressionsfaktor F** = Originalgrösse / Komprimierte Grösse

**VLC Variable Length Code** unterschiedlich Codelängen von Zeichen werden minimiert. Ein Beispiel davon ist der Morsecode da es meistens eine kürzere Codelänge für alle Zeichen gebraucht wird.  
Morsecode braucht es einen Trennzeichen oder Delimiter, der eine Pause sein würde.  

Huffman-Code zuerst die Häufigkeit berechnen. 

**RLC Run-Length-En/Coding**

**LZW Lempel-Ziv-Welch**

## Verlustbehaftete Kompression  

**JPEG-Bildkomprimierung** Joint Photographic Experts Group. ISO/IEC 10918-1. JPEG Komprimierung erlaubt 90% Kompressionsrate ohne sichtbare Informationsverlust.

Eine Artifakte bei Bildkomprimierung sind sichtbare Unvollkommenheiten (imperfections), die beim rendering entstehen.

Die einfachsten Komprimierungsverfahren sind die Reduktion der Bildgrösse oder der Farbigkeit

**Luminanz**
**Chrominanz**

**Der Prozess von JPEG-Kompressions-Verfahren**

**MPEG**
**Intra- und Inter-Frame-Kompression**

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

**Cäsar-Verschlüsselung** (Rotationschiffre) jede lateinische Buchstaben des Alphabets wird **um N Stellen rotiert oder besser gesagt ersetzt**. Beispiel ROT-13, es verschieben sich Buchstaben um 13 nächsten Buchstaben.

Mit dem **CrypTool** zu **entschlüsseln**, Text eingeben. In den Tabs "Analyse/Symetrische Verschlüsselung (klassisch)/Cipher-Text Only/Caesar or whatever the algorithm is/Entschlüsseln where the Ermittelter Caesar-Schlüssel ist"
