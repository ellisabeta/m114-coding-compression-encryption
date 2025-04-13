# m114 Kompressionen

## Kompression
Kompressionsverfahren vor allem bei Bildern, ist wenn der urpsrüngliche Daten reduziert werden. Meistens um redundante Informationen zu entfernen. Umgekehrter Prozess ist Dekompression (Dekomprimierung).  
Verlustfreie Komprimierung, ist wenn alle Originaldaten zurück gewonnen werden können. Komprimierung = weniger Platz.

**Komprimierungsgrad bestimmen**:  
**Kompressionsrate K** = (Originalgrösse - Komprimierte Grösse) / OriginalGrösse  
**Kompressionsfaktor F** = Originalgrösse / Komprimierte Grösse

**VLC Variable Length Code** unterschiedlich Codelängen von Zeichen werden minimiert.  
Ein Beispiel davon ist der Morsecode da es meistens eine kürzere Codelänge für alle Zeichen gebraucht wird.  
Das andere wäre der Huffman-Code.

**Huffman-Code berechnen**  
Huffman-Code &rarr; Wort und Wort &rarr; Huffman-Code:  
Wort zu Huffman code muss man einen binären Baum erstellen. Dabei muss man eine Codetabelle haben.  
**Vorgehensweise**:
1. zuerst die Häufigkeit der Buchstaben zählen.
2. einen binären Baum erstellen nach der Häufigkeit, meistens links am häufigsten und rechts weniger häufigere Buchstaben
3. Buchstaben, die am wenigsten vorkommen, werden zu einem Knoten "^", man addiert zusammen die Häufigkeit
4. so geht man bis ganz zum letzten Buchstaben mit der grössten Häufigkeit
5. dann die Äste beschriften, nach links ist 1 nach rechts 0
6. dann erstellt man eine Codetabelle anhand dem Baum mit den binären Ästen  
**Wichtig** bei Punkt 3. muss man zuerst immer die kleinste Häufigkeit zuerst zusammen zählen.

**Umgekehrt**:
1. Falls du den Baum nicht hast, brauchst du die Codetabelle, um ihn wieder aufzubauen.
2. Starte von der Wurzel des Baums und bewege dich nach links (1) oder rechts (0), je nach nächstem Bit.
3. Sobald du ein Buchstabe erreichst, notiere den Buchstaben und springe zurück zur Wurzel.
4. Lies die nächsten Bits und wiederhole den Vorgang.  
Die Zahl: 0111001000100000111, zuerst geht es nach rechts (0) ist kein Buchstabe und dann zu (1) links, also das ist die erste Buchstabe, dann (1) mal nach links, ist schon die nächste Buchstabe, dann wieder das gleiche usw.

**RLC Run-Length-En/DeCoding**  
RLC ist eine Lauflängenkodierung. Es wird die Stelle markiert, wenn ein Symbol sich in der Nachricht verändert.  
**Vorgehensweise**:
1. auf jeder Linie Pixel durchzählen bis Wechsel. Wenn es auf der ersten und zweiten Zeile immer noch nur weisse gibt, dann diese Anzahl bis die schwarzen vorkommen.  
Beispiel: Ab erstem Pixel oben links: 31 x Weiss, 2 x Schwarz, 11 x Weiss, 3 x Schwarz, 2 x Weiss, 6 x Schwarz, 6 x Weiss, 6 x Schwarz, 1 x Weiss, 8 x Schwarz, 4 x Weiss
2. für jede Zeile wiederholen.
3. die grösste Zahl von allen in dem Fall 31 müssen wir in Binär darstellen. Um zu wissen wie viele Bits für die Zahl wir brauchen macht man: log(31 + 1) / log​(2) = 5 Bits
4. Anzahl bits pro Zahl von der Formel: 5 Bits. Alle andere Ziffern mit Bits darstellen
5. Die Zahlen im 5-Bit Binärcode (d.h. beginnt mit Weiss und jedesmal ein Wechsel): 11111 00010 01011 00011 00010 00110 00110 00001 01000 00100.

**LZW Lempel-Ziv-Welch**
0..255 Bits ASCII Zeichen, ab 256 Buchstaben ins Wörterbuch. Die Tabelle lautet: Zeichenkette, (Eingang von Text) Gefunden, Gespeichert, Temporärer Wörterbuch.  
![screenshot](./Aufgaben/images/LZW_transformation.png)

## Verlustbehaftete Kompression  

Es kommt zu einem Datenverlust bei einer Kompression wenn beim Dekomrimieren entsteht das 100% Abbild des Originals nicht mehr.

**Komprimierungsverfahren** = die Reduktion der Bildgrösser oder der Farbigkeit.

**JPEG-Bildkomprimierung** Joint Photographic Experts Group. ISO/IEC 10918-1. JPEG Komprimierung erlaubt 90% Kompressionsrate ohne sichtbaren Informationsverlust. Eine Artifakte bei Bildkomprimierung sind sichtbare Unvollkommenheiten (imperfections), die beim rendering entstehen.  
Bei hoher Kompression treten folgende Nachteile auf: Unsaubere Textkonturen, Blockartefakte

Die 5 Schritte:
1. Umwandung des Farbraums / Color Space Conversion
2. Chrominanz Unterabtastung / Chrominance Downsampling
3. Diskrete Kosinus Transformation / Discrete Cosine Transformation
4. Quantisierung / Quantization
5. Zick-Zack & RLC & VLC 

**Luminanz** (Y) Luminanz beschreibt die Helligkeitsinformation eines Bildes. Wie hell oder dunkel ein Pixel ist.  
**Chrominanz** (Cr oder Cb) Chrominanz beschreibt die Farbanteile eines Bildes.Da das menschliche Auge Farbunterschiede weniger genau wahrnimmt als Helligkeitsunterschiede, können Chrominanz-Informationen stärker komprimiert werden. Ist die zentrale Technik in der JPEG-Komprimierung.  
**Cb** (Blue-Difference Chrominance): wie stark die Farbe Blau vom Helligkeitswert abweicht.  
**Cr** (Red-Difference Chrominance): wie stark die Farbe Rot vom Helligkeitswert abweicht.

**Der Prozess von JPEG-Kompressions-Verfahren**  
Ein wichtiger Schritt in der JPEG-Kompression ist die Umwandlung des Bildes vom RGB- in den YCrCb-Farbraum. Unterstützt True-Color. Ist verlustbehaftet komprimiert. Die Komprimierung erfolgt hauptsächlich durch Subsampling und Quantisierung (DCT).

**DCT** Diskrete Cosinus Transformation  
Ist eine der Haupttechniken der JPEG-Komprimierung und dient der Umwandlung von Bildinformationen in Frequenzbereiche zur besseren Datenreduktion.

**MPEG**  
Moving Picture Experts Group (MPEG). Die MPEG-Komprimierung basiert auf Intra- und Inter-Frame-Kompression.  
**Intra- und Inter-Frame-Kompression**  
Intraframe-Kompression reduziert die Bildinformationen ähnlich wie das JPEG-Verfahren.  
Interframe-Kompression wird durch die Differenzbildung von Bildbereichen erreicht.  

**GOP** = Group Of Pictures.  
Damit ist eine Bildgruppe gemeint, die mit einem Schlüsselbild (I-Frame oder Vollbild) beginnt. Danach folgen eine gewissen Anzahl B-Frames und P-Frames, bis wieder eine neue Bildgruppe mit startendem I-Frame folgt.

**I-Frame, P-Frame, B-Frame**
I-Frame → Intraframe-Kompression
P-Frame → Interframe-Kompression
I-Frame → Benutzt DCT zur Kompression
P-Frame → Benutzt nur DPCM zur Kompression
B-Frame → Benutzt bidirektionale Vorhersage zur differenziellen Kompression
