# Tag 2

## Zahlensysteme

### Binärsystem
### Hexadezimahlsystem
### Dezimahlsystem
## Zahlenumwandlung
27=0001 1011
1001 0111=147
1011 0111=B7
3D=61
27=0001 1011
1001 0011=-109

## Datentypen

Wenn man in einem Programm, einer Tabellenkalkulation oder einer Datenbank eine Variable erstellt, muss man einen Datentyp wählen.
Einfache numerische Datentypen
• INTEGER (signed): ganze Zahlen mit Vorzeichen, z. B. –2, –1, 0, 1, 2. In Java: int = 32 Bit, long = 64 Bit.
• INTEGER (unsigned): ganze positive Zahlen ohne Vorzeichen.
• FLOAT: Fliesskommazahlen, z. B. –2.1426. In Java: float = 32 Bit, double = 64 Bit.
• BOOLEAN: logischer Wert, true oder false.
Einfache alphanumerische Datentypen
• CHARACTER (char): ein einzelnes Textzeichen, z. B. A, b, 7, ?, +.
Zusammengesetzte Datentypen
• STRING / VARCHAR: eine Textzeile, also ein Array aus Characters, z. B. «Hello World!».

Welcher Datentyp eignet sich?
| Situation | Datentyp | Begründung |
|---|---|---|
| Ameiseninvasion zählen | Integer (unsigned) | ganze Zahlen, nie negativ |
| Etagen zählen | Integer (signed) | Untergeschosse sind negativ (z. B. Tiefgarage = –1) |
| Geburtstagstorte teilen | Float | Bruchteile wie 1/3 |
| Entscheiden über Go / NoGo | Boolean | nur zwei Zustände |
| Text schreiben | Char bzw. String | Zeichen und Zeichenketten |


## Datentypen und Wertebereich

 Aufgaben zu Datentypen und Wertebereich
1. Wertebereich 16 Bit unsigned: 2<sup>16</sup> = 65'536 Werte → 0 bis 65'535
2. Wertebereich 16 Bit signed: –32'768 bis +32'767
3. Zeichen bei 8-Bit-Character: 2<sup>8</sup> = 256 Zeichen
4. Minimale Bits für 0 bis 999'999: 2<sup>19</sup> = 524'288 (zu klein), 2<sup>20</sup> = 1'048'576 (reicht) → 20 Bit
5. Minimale Bits für –999 bis +999: Anzahl Werte = 999 + 999 + 1 = 1'999. 2<sup>10</sup> = 1'024 (zu klein), 2<sup>11</sup> = 2'048 (reicht) → 11 Bit
6. Redundanz bei 0 bis 999 mit 16 Bit: Für 1'000 Werte braucht man minimal 10 Bit (2<sup>10</sup> = 1'024). Gespeichert werden 16 Bit. Redundanz = 16 – 10 = 6 Bit
7. Binärzahl 101101<sub>B</sub> normalisieren: Das Komma wird hinter die erste 1 geschoben (5 Stellen nach links): 101101<sub>B</sub> = 1.01101<sub>B</sub> · 2<sup>5</sup>
8. Float (32 Bit) mit 300'000'000, dann +1: Die Mantisse hat nur 24 signifikante Bits (23 gespeicherte + 1 implizite). 300'000'000 liegt zwischen 2<sup>28</sup> und 2<sup>29</sup>. Dort beträgt der Abstand zwischen zwei darstellbaren Zahlen 2<sup>28–23</sup> = 32. Die Zahl 300'000'001 liegt nicht auf diesem Raster und wird auf die nächste darstellbare Zahl gerundet. Das ist wieder 300'000'000. Gespeichert wird also weiterhin 300'000'000. Die +1 geht verloren. Float ist bei grossen Zahlen nicht mehr auf eine Einheit genau.
9. Kundenkartei mit 100'000 Booleans:
• Theoretisch minimal: 1 Bit pro Eintrag → 100'000 Bit = 12'500 Byte (ca. 12.5 kB)
• Real (1 Byte pro Boolean): 100'000 Byte = 100 kB
• Das ist 8-mal mehr als nötig.
10. Wochentag als INTEGER (4 Byte) bei 5 Mio. Datensätzen: Das ist nicht zweckmässig:
• Es kommen nur die Werte 1–7 vor. Dafür reichen 3 Bit bzw. 1 Byte.
• 5 Mio. × 4 Byte = 20 MB, mit einem 1-Byte-Typ (z. B. TINYINT) nur 5 MB.
• Besser: kleinerer Datentyp oder ein Aufzählungstyp (ENUM).
• Gegenargument: Bei kleinen Datenmengen spielt der Unterschied keine grosse Rolle, bei 5 Mio. Datensätzen aber schon.

 ## Wo wird UTF-8, wo UTF-16 eingesetzt?
• UTF-8: Internet (HTML, E-Mail, JSON), Linux/macOS, die meisten Textdateien und Programmiersprachen-Quellcode.
• UTF-16: intern in Windows, in Java- und .NET-Strings und in JavaScript.
2. Was bedeutet die Byteorder bei UTF-16? Sie legt fest, in welcher Reihenfolge die zwei Bytes eines 16-Bit-Zeichens gespeichert werden (Big Endian: hoch zuerst, Little Endian: tief zuerst). Mit dem BOM (FE FF bzw. FF FE) erkennt das Programm die richtige Reihenfolge.
3. Was bedeutet «abwärtskompatibel» bei UTF-8? Ein reiner ASCII-Text (Zeichen 0–127) ist in UTF-8 byte-identisch mit dem ASCII-Text. Alte Programme können solche Texte darum weiterhin lesen. Bei UTF-16 gibt es das nicht: Auch ein «A» braucht 2 Byte (00 41), also ist ein ASCII-Text in UTF-16 nicht mehr ASCII-lesbar.
4. Speicherbedarf bei deutschem/englischem Text:
• ISO 8859: immer 1 Byte pro Zeichen → am kleinsten
• UTF-8: 1 Byte pro Zeichen, nur Umlaute und ß brauchen 2 Byte → fast gleich klein
• UTF-16: 2 Byte pro Zeichen → ca. doppelt so gross
5. Wann wird UTF-16 vier Byte lang? Bei Zeichen ab U+10000 (ausserhalb der Basic Multilingual Plane), z. B. Emojis, seltene Schriftzeichen oder Musiksymbole. Sie werden als Surrogate-Paar (High Surrogate + Low Surrogate) gespeichert.
6. Zeichen mit bekanntem Unicode in Word eingeben (z. B. €): In Word den Hex-Code 20AC tippen und danach Alt + C drücken. Dann wird der Code in das Zeichen € umgewandelt. Alternativ: Einfügen → Symbol.
7. Problem beim Violinschlüssel (𝄞, U+1D11E): Der Code hat 5 Hex-Stellen und liegt ausserhalb von U+FFFF. Er braucht in UTF-16 ein Surrogate-Paar (D834 DD1E), also 4 Byte. Das ist komplizierter. Ausserdem muss die gewählte Schriftart das Zeichen enthalten, sonst erscheint nur ein Kästchen oder Fragezeichen.
8. UTF-8-Bitcode für ® (U+00AE): U+00AE liegt im Bereich 0080–07FF, also 2 Byte: 110xxxxx 10xxxxxx. 00AE = 1010'1110 → 1100'0010 1010'1110 (hex: C2 AE)
