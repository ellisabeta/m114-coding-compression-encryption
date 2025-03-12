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

**Signed and Unsigned** Wenn eine Zahl negativ ist, ist sie **signed**. Alle unsigned Zahlen sind positiv und gehen von 0 bis 255. Alle (Zweierkomplement) signed Zahlen sind negativ und gehen von -128 bis 127.  
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
**Gleitkommazahlen** ermöglichen sehr grosse Zahlenformate mit grossem Wertebereich, wie single und double. Gleitkommaformat ist in IEEE-754 Format. Vorzeichen, Exponent, Mantisse  
**Alphanumerische Code** Dient dazu da um Text zu codieren.  
ASCII-Code:
ISO-8859 and ANSI Code:
Unicode UTF-8:

**Vier UTF-8 Zeichen codes**: 

## Bildcodierung
PPI = pixel per inch  
DPI = dots per inch

**Farbräume**
Die 4 Farbräume sind:
- RGB (red green blue)
- CMYK (cyan magenta yellow keycolor=black)
- HSL
- YUV ()

**Vektorgrafik**

**Alphakanal Transparenz**

## Kompression
Kompressionsverfahren vor allem bei Bildern, ist wenn der urpsrüngliche Daten reduziert werden.  
**Kompressionsrate K** = (Originalgrösse - Komprimierte Grösse) / OriginalGrösse  
**Kompressionsfaktor F** = Originalgrösse / Komprimierte Grösse

**VLC Variable Length Code**

**RLC Run-Length-En/Coding**

**LZW Lempel-Ziv-Welch**


SI-Präfixe 10er System:  
1024 → [Y] → Yotta → 1024 → 1'000'000'000'000'000'000'000'000 → Quadrillion  
1021 → [Z] → Zetta → 1021 → 1'000'000'000'000'000'000'000 → Trilliarde  
1018 → [E] → Exa  → 1'000'000'000'000'000'000 → Trillion  
1015 → [P] → Peta  → 1'000'000'000'000'000 → Billiarde  
1012 → [T] → Tera  → 1'000'000'000'000 → Billion  
109 → [G] → Giga  → 1'000'000'000 → Milliarde  
106 → [M] → Mega  → 1'000'000 → Million  
103 → [k] → kilo → 1'000 → Tausend  
100 → [-]  → 1 → Eins  
10-3 → [m] → milli  → 0.001 → Tausendstel  
10-6 → [µ] → mikro  → 0.000'001 → Millionstel  
10-9 → [n] → nano  → 0.000'000'001 → Milliardstel  
10-12 → [p] → piko  → 0.000'000'000'001 → Billionstel  
10-15 → [f] → femto  → 0.000'000'000'000'001 → Billiardstel  
10-18 → [a] → atto  → 0.000'000'000'000'000'001 → Trillionstel  

IEC-Präfixe (2er System):  
280 → [Yi] → Yobi → 1'208'925'819'614'629'174'706'176  
270 → [Zi] → Zebi → 1'180'591'620'717'411'303'424  
260 → [Ei] → Exbi → 1'152'921'504'606'846'976  
250 → [Pi] → Pebi → 1'125'899'906'842'624  
240 → [Ti] → Tebi → 1'099'511'627'776  
230 → [Gi] → Gibi → 1'073'741'824  
220 → [Mi] → Mebi → 1'048'576  
210 → [Ki] → Kibi → 1'024  
