# Tag 3

# Aufgaben zu Unicode

## 1. Wo wird UTF-8 eingesetzt, wo UTF-16?

- **UTF-8:** Wird vor allem im Internet, auf Webseiten, in E-Mails und in vielen Programmiersprachen verwendet.
- **UTF-16:** Wird unter anderem in Windows, Java und bestimmten Programmen zur internen Textverarbeitung verwendet.

## 2. Was bedeutet die Byteorder bei UTF-16?

Die Byteorder beschreibt die Reihenfolge, in der die Bytes eines Zeichens gespeichert werden.

Es gibt zwei Varianten:

- **Big Endian (BE):** Das wichtigste Byte wird zuerst gespeichert.
- **Little Endian (LE):** Das unwichtigste Byte wird zuerst gespeichert.

Beispiel: Das Zeichen `A` hat den Unicode `U+0041`.

| Byteorder | Bytefolge |
|---|---|
| Big Endian | `00 41` |
| Little Endian | `41 00` |

Die Byteorder muss bekannt sein, damit der Computer die Zeichen richtig lesen kann.

## 3. Was bedeutet «abwärtskompatibel» bei UTF-8? Existiert diese Abwärtskompatibilität auch bei UTF-16?

Abwärtskompatibel bedeutet, dass ältere Daten und Systeme weiterhin funktionieren.

- **UTF-8:** Die ersten 128 Zeichen sind identisch mit ASCII. Deshalb können alte ASCII-Texte problemlos als UTF-8 gelesen werden.
- **UTF-16:** Ist nicht abwärtskompatibel mit ASCII, da die Zeichen normalerweise mindestens zwei Byte benötigen.

**Fazit:** UTF-8 ist zu ASCII abwärtskompatibel, UTF-16 nicht.

## 4. Wie beurteilen Sie den Speicherbedarf von deutsch- oder englischsprachigem Text bei ISO-8859-Codierung, UTF-8 und UTF-16?

