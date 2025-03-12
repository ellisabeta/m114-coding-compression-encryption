# m114

### Datenspeicher und Datenübertragung
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

**Signed and Unsigned** Wenn eine Zahl negativ ist, ist sie **signed**. Alle unsigned Zahlen sind positiv und gehen von 0 bis 255. Alle (Zweierkomplement) signed Zahlen sind negativ und gehen von -128 bis 127.  
n= Bit stellen
*Signed Formel*: (min) -2^(n-1), (max) 2^(n-1)-1
*Unsigned Formel*: (min) 0, (max) 2^n -1

**MSB**: most significant bit = höchswertige Bit entweder 255 oder 127
**LSB**: least significant bit = niedrigstwertiges Bit entweder 0 oder -128

**Zahlensystem** bin &rarr; dez = (dez num)v10 = (binary number * 2^position of binary number) + (bv1 * 2^1) + (bv2 * 2^2)... so for 1011 it will be 1*2^3 + 0*2^2 + 1*2^1 + 1*2^0 = 8+0+2+1= 11  
dez &rarr; bin = dez/2 rest is the binary numbers  
bin &rarr; hex = from lsb add up the bin stellen zusammen 0111 = 0 4 2 1 = 7  
hex &rarr; dez = (n*16^3) + (n*16^2) + (n*16^1) + (n*16^0) potenz 0 gibt immer 1

### Codesysteme
Code bedeutet eine Zuordnung oder Abbildung der Zeichen von der ersten "Character set" und dem zweiten "Character set" zu einander.

#### Alphanumerische Code
Dient dazu da um Text zu codieren.  
ASCII-Code:


### Bildcodierung
PPI = pixel per inch  
DPI = dots per inch

### Farbräume:
Die 4 Farbräume sind:
- RGB (red green blue)
- CMYK (cyan magenta yellow keycolor=black)
- HSL
- YUV ()

### Kompression
Kompressionsverfahren vor allem bei Bildern, ist wenn der urpsrüngliche Daten reduziert werden.  

Kompressionsrate **K** = (Originalgrösse - Komprimierte Grösse) / OriginalGrösse  
Kompressionsfaktor **F** = Originalgrösse / Komprimierte Grösse


- Für Kalkulationen brauche den Scientific und Programmer Rechner auf Windows