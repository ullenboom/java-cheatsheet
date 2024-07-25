Ein umfassendes und leicht verständliches Cheat Sheet für Java-Entwickler. Diese Sammlung von Snippets, Tipps und Best Practices deckt die grundlegenden bis fortgeschrittenen Java-Konzepte ab und bietet schnelle Referenzen für häufig verwendete Syntax und Funktionen. Perfekt für Anfänger, die Java lernen, sowie Umsteiger, die ihr Wissen auffrischen möchten.

```java
@SuppressWarnings( "all" )
public class Cheatsheet {
  public static void main( String[] args ) {
    ///
    /// Java Datentypen, Literale
    ///
    {
      // Ganzzahlen
      byte octet = 100;              // 8-bit, Bereich: -128 bis 127
      short s = 10000;               // 16-bit, Bereich: -32,768 bis 32,767
      int i = 100000;                // 32-bit, Bereich: -2^31 bis 2^31-1
      long l = 1000000000000L;       // 64-bit, Bereich: -2^63 bis 2^63-1
      //                   ☝️           Long Literale haben L oder l am Ende

      // Fließkommazahlen
      double d = 3.14159265359;      // 64-bit IEEE 754 (Standard für Dezimalzahlen)
      float f = 3.14f;               // 32-bit IEEE 754
      //           ☝️                   Float-Literale haben F oder f am Ende.

      // Einzelne Zeichen
      char c = 'A';                  // 16-bit Unicode Zeichen
      //       ☝️                       Einzelnde Zeichen in einzelnen Anführungszeichen

      // Boolesche Werte
      boolean bool = true;           // true oder false

      // String
      String str = "Strings stehen in 'doppelten' Anführungszeichen";
      //          ☝️ ️

      String muliline = """
                       ☝️ Mehrzeilige Zeichenketten beginnnen mit drei ".    
          Und dann folgt ein Zeilenumbruch.""";

      // Finale (Konstante) Variablen
      final double PI = 3.14159;    // Konstante (kann nicht geändert werden)

      // Literal-Notationen
      int binary = 0b1010_1010;  // 170 in Dezimal
      //           ☝️
      int hex = 0xA5;            // 165 in Dezimal
      //        ☝️
      int oktal = 0777;          // 511 in Dezimal
      //         ☝️️
      int million = 1_000_000;   // Unterstriche machen große Zahlen lesbarer
      //            ☝️  ☝️
      double pi = 3.14_15_92;
      long big = 1_234_567_890_123L;  // long mit L-Suffix
    }

    ///
    /// Operatoren und Operanden
    ///
    {
      int a = 10, b = 3;
      // Arithmetische Operatoren
      System.out.println( a + b );  // 13
      System.out.println( a - b );  // 7
      System.out.println( a * b );  // 30
      System.out.println( a / b );  // 3
      System.out.println( a % b );  // 1
      System.out.println( ++a );    // 11
      System.out.println( --b );    // 2

      int c;
      // Zuweisungsoperatoren
      c = 15;
      System.out.println( c += 5 ); // 20
      System.out.println( c -= 5 ); // 15
      System.out.println( c *= 2 ); // 30
      System.out.println( c /= 3 ); // 10
      System.out.println( c %= 4 ); // 2

      // Vergleichsoperatoren
      System.out.println( 1 == 2 ); // false
      System.out.println( 1 != 2 ); // true
      System.out.println( 2 > 1 );  // true
      System.out.println( 2 < 1 );  // false
      System.out.println( 1 >= 1 ); // true
      System.out.println( 2 <= 1 ); // false

      // Logische Operatoren
      System.out.println( !true );         // false (NICHT)
      System.out.println( true && false ); // false (UND)
      System.out.println( true || false ); // true  (ODER)
      System.out.println( true ^ false );  // true  (logisches XOR)
      System.out.println( true ^ true );   // false

      // Bitweise Operatoren
      int m = 0b1010_1010;   //  170 in Dezimal
      int n = 0b0011_1100;   //   60 in Dezimal
      int p = -0b1010_1010;  // -170 in Dezimal

      System.out.println( m & n );   // 44  (0b0010_1000)
      System.out.println( m | n );   // 186 (0b1011_1110)
      System.out.println( m ^ n );   // 142 (0b1001_0110)
      System.out.println( ~m );      // -171 (0b1111_1111_1111_1111_1111_1111_0101_0101)
      System.out.println( m << 2 );  // 680 (0b10_1010_1000)
      System.out.println( m >> 2 );  // 42  (0b0010_1010)
      System.out.println( m >>> 2 ); // 42  (0b0010_1010)
      System.out.println( p >> 2 );  // -43 (0b1111_1111_1111_1111_1111_1111_1101_0110)
      System.out.println( p >>> 2 ); // 1073741781 (0b0011_1111_1111_1111_1111_1111_1101_0110)

      // Bedingungsoperator
      // ergebnis = booleanBedingung ? wertWennWahr : wertWennFalsch;
      double f = 12, g = 22;
      double max = f > g ? f : g;      // 22

      // Implizite Typumwandlung (Widening Casting)
      long longVal = 1;                   // int zu long
      float floatVal = 12345678901234L;   // long zu float
      double doubleVal = floatVal;        // float zu double
      int charCode = 'A';                 // char zu int

      // Explizite Typumwandlung (Narrowing Casting)
      double doubleNum = 9.78;
      float floatNum = (float) doubleNum;     // double zu float
      //                ☝️                       Zieltyp in runden Klammern vor Ausdruck
      long longNum = (long) floatNum;         // float zu long
      int intNum = (int) longNum;             // long zu int
      short shortNum = (short) intNum;        // int zu short
      byte byteNum = (byte) shortNum;         // short zu byte
      char charVal = (char) charCode;         // int zu char
    }

    ///
    /// Fallunterscheidungen
    ///

    // Bedingte Anweisungen mit if-else
    int score = 75;

    if ( score >= 90 ) {               // 👈 Bedingung muss vom Typ boolean sein
      System.out.println( "Note: A" ); // 👈 Code, wenn Bedingung wahr ist
    }
    // else if ( andereBooleanBedingung ) {
    else if ( score >= 60 ) {
      System.out.println( "Note: B" ); // 👈 Code, wenn andere Bedingung wahr ist
    }
    else {
      System.out.println( "Note: C" ); // 👈 Code, wenn keine Bedingung wahr ist
    }
    // -> Note: B

    // Switch

    String day = "MONDAY";
    // switch-Anweisung mit ->
    switch ( day ) {
      case null -> throw new IllegalStateException();
      //   ☝️   case null fängt null-Referenz ab
      case "MONDAY", "FRIDAY", "SUNDAY" -> System.out.println( "Busy day" );
      //          ☝️  ️Mehrere Fälle mit Komma abtrennen
      case "TUESDAY" -> System.out.println( "Productive day" );
      case "WEDNESDAY", "THURSDAY" -> System.out.println( "Normal day" );
      case "SATURDAY" -> System.out.println( "Lazy day" );
      default -> System.out.println( "Invalid day" );
      // ☝️     default deckt ab, was die anderen case nicht abgedeckt haben
    }

    // switch-Ausdruck mit ->
    System.out.println( switch ( day ) {
      case "MONDAY", "FRIDAY", "SUNDAY" -> "Busy day";
      case "TUESDAY" -> "Productive day";
      case "WEDNESDAY", "THURSDAY" -> "Normal day";
      case "SATURDAY" -> {
        String result = "Lazy day";
        yield result;
        //☝️  yield nutzen, wenn rechts vom Pfeil kein direkter Ausdruck steht
      }
      case null, default -> "Invalid day";
      //       ☝️        null und default kann man mit case und Komma zusammenfasen
    } );

    ///
    /// Schleifen
    ///

    // While-Schleife, Erst Prüfung vor ersten Durchlauf
    while ( Math.random() < 0.2 ) {  // 👈 Bedingung muss vom Typ boolean sein
      // Wiederholter Code
    }

    // Do-While-Schleife, mindestens ein Durchlauf, dann Prüfung auf weitere Durchläufe
    do {
      // Wiederholter Code
    } while ( Math.random() < 0.2 ); // 👈 Bedingung muss vom Typ boolean sein

    // For-Schleife
    for ( int i = 0; i < 10; i++ ) {
      //    ☝️                       Einmalige Initialisierung
      //             ☝️              Bedingung muss vom Typ boolean sein, vor jedem Schleifendurchlauf
      //                      ☝️     Am Ende jedes Schleifendurchlaufs
      // Wiederholter Code
    }

    //    break;      // Beendet die aktuelle Schleife oder switch-Anweisung
    //    continue;   // Springt zum nächsten Schleifendurchlauf
    //    return;     // Beendet die Methode und gibt optional einen Wert zurück

    ///
    /// Arrays
    ///

    // Arrays deklarieren und Array-Literal-Notation
    int[] intArray = { 1, 2, 3, 4, 5 };              // Array von Ganzzahlen
    String[] stringArray = new String[ 5 ];          // Array von Strings mit Länge 5
    int[][] zweiDArray = { { 1, 2 }, { 3, 4 }, { 5, 6 } }; // Zweidimensionales Array

    ///
    /// Objekte
    ///

    int intPrim = 42;
    Integer intObj = Integer.valueOf( intPrim );  // Explizites Boxing
    Integer intAutoboxed = 42;
    //                     ☝️                        Autoboxing (Primitiv -> Wrapper)
    int intUnboxed = intObj;
    //                ☝️                             Unboxing (Wrapper -> Primitiv)
    Integer nullableInt = null;
    // System.out.println( nullableInt * 2 );
    //                     ☝️                        Führt zu einer NullPointerException

    Integer a = 127, b = 127, c = 128, d = 128;
    System.out.println( a == b );                 // true (Caching -128 bis 127)
    System.out.println( c == d );                 // false
    System.out.println( c.equals( d ) );          // true

  }
}
```
