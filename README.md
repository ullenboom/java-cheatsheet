Ein umfassendes und leicht verständliches Cheat Sheet für Java-Entwickler. Diese Sammlung von Snippets, Tipps und Best Practices deckt die grundlegenden bis fortgeschrittenen Java-Konzepte ab und bietet schnelle Referenzen für häufig verwendete Syntax und Funktionen. Perfekt für Anfänger, die Java lernen, sowie Umsteiger, die ihr Wissen auffrischen möchten.

```java
import java.util.Arrays;

@SuppressWarnings( "all" )
public class Cheatsheet {
  public static void main( String[] args ) {
    ///
    /// Java Datentypen, Literale
    ///
    {
      // Ganzzahlen
      byte octet = 100;              // 8-Bit, Bereich: -128 bis 127
      short s = 10000;               // 16-Bit, Bereich: -32,768 bis 32,767
      int i = 100000;                // 32-Bit, Bereich: -2^31 bis 2^31-1
      long l = 1000000000000L;       // 64-Bit, Bereich: -2^63 bis 2^63-1
      //                   ☝️           Long Literale haben L oder l am Ende

      // Fließkommazahlen
      double d = 3.14159265359;      // 64-bit IEEE 754 (Standard für Fließkommazahlen)
      float f = 3.14f;               // 32-bit IEEE 754
      //           ☝️                   Float-Literale haben F oder f am Ende.

      // Einzelne Zeichen
      char c = 'A';                  // 16-bit Unicode Zeichen
      //       ☝️                       Einzelne Zeichen in einzelnen Anführungszeichen

      // Boolesche Werte
      boolean bool = true;           // true oder false

      // String
      String str = "Strings stehen in 'doppelten' Anführungszeichen";
      //          ☝️ ️

      String multiline = """
                        ☝️ Mehrzeilige Zeichenketten beginnen mit drei ".    
          Und dann folgt ein Zeilenumbruch.""";

      // Finale (Konstante) Variablen
      final double PI = 3.14159;  // Konstante (kann nicht geändert werden)

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
      //       ☝️        null und default kann man mit case und Komma zusammenfassen
    } );

    ///
    /// Schleifen
    ///

    // While-Schleife, erst Prüfung vor ersten Durchlauf
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
  }
}

@SuppressWarnings( "all" )
class ClassNewReferencesNullExamples {
  public static void main( String[] args ) {
    new StringBuilder();
    //☝️           Neue Instanz der Klasse StringBuilder wird mit new erstellt

    StringBuilder stringBuilder;        // Deklaration einer Referenzvariablen

    stringBuilder = new StringBuilder(); // Initialisieren einer Variablen mit neuer Instanz

    StringBuilder stringBuilder2 = new StringBuilder(); // Deklaration und Initialisierung

    StringBuilder anotherRef = stringBuilder;            // Referenz kopieren

    // Zugreifen auf Objektmethoden und -variablen
    stringBuilder.append( 1 );                           // Aufrufen einer Methode des Objekts
    java.awt.Point point = new java.awt.Point();
    point.x = 10;                                        // Setzen einer Objektvariablen
    point.y = point.x;                                   // Auslesen und Setzen einer Objektvariablen

    /// null-Verweise
    StringBuilder nullObject = null;                     // Referenz zeigt auf kein Objekt

    if ( nullObject == null ) {                          // Prüfen, ob eine Referenz null ist
      System.out.println( "Referenz ist null" );
    }

    // Prüfen, ob eine Referenz nicht null ist, um NullPointerException zu vermeiden
    if ( stringBuilder != null ) {
      stringBuilder.toString();                       // Methode nur aufrufen, wenn das Objekt existiert
    }
  }
}

@SuppressWarnings( "all" )
class ArrayExamples {
  public static void main( String[] args ) {
    // Arrays deklarieren und Array-Literal-Notation
    int[] intArray = { 1, 2, 3, 4, 5 };              // Array von Ganzzahlen
    String[] stringArray = new String[ 5 ];          // Array von Strings mit Länge 5
    int[][] twoDArray = { { 1, 2 }, { 3, 4 }, { 5, 6 } }; // Zweidimensionales Array

    // Auf Array-Elemente zugreifen
    int firstElement = intArray[ 0 ];                // Erstes Element des Arrays
    stringArray[ 0 ] = "Hello";                      // Erstes Element setzen
    int arrayLength = intArray.length;               // Länge des Arrays ermitteln, 5

    // Über Arrays iterieren
    for ( int i = 0; i < intArray.length; i++ ) {    // Variante 1
      System.out.println( intArray[ i ] );           // Element per Indexzugriff ausgeben
    }

    for ( int value : intArray ) {                   // Variante 2: Erweitere for-Schleife
      System.out.println( value );                   // Der Index steht nicht zur Verfügung
    }

    // java.util.Arrays ist eine Utiltiy-Klasse
    Arrays.fill( intArray, 42 );                     // Alle Elemente des Arrays auf 42 setzen
    Arrays.sort( intArray );                         // Sortieren in aufsteigender Reihenfolge
    Arrays.sort( stringArray );                      // String-Array alphabetisch sortieren
    // Binäre Suche im sortierten Array, -1 wenn nicht gefunden
    int index = Arrays.binarySearch( intArray, 3 );
    int[] copiedArray = Arrays.copyOf( intArray, intArray.length ); // Ganzes Array kopieren
    int[] partialCopy = Arrays.copyOfRange( intArray, 1,
                                            3 );       // Teilbereich des Arrays kopieren
    // Array zu String umwandeln: [1, 2, 3, 4, 5]
    String arrayAsString = Arrays.toString( intArray );

    // Mehrdimensionale Arrays
    int[][] matrix = new int[ 3 ][ 3 ];                  // Zweidimensionales Array (Matrix) deklarieren
    matrix[ 0 ][ 0 ] = 1;                                // Element setzen

    int[][][] threeDArray = new int[ 2 ][ 2 ][ 2 ];      // Dreidimensionales Array 2x2x2

    /// Mehrdimensionale Arrays iterieren
    for ( int i = 0; i < matrix.length; i++ ) {
      for ( int j = 0; j < matrix[ i ].length; j++ ) {
        System.out.print( matrix[ i ][ j ] + " " );
      }
      System.out.println();
    }
  }

  static void printInfo( String name, int... scores ) {
    //                                   ☝️  Methode mit Varargs
    System.out.println( "Name: " + name );
    System.out.println( "Scores: " + Arrays.toString( scores ) );

    // Varargs aufrufen
    // printInfo( "Jill" );
    // printInfo( "Joe", 75, 80 );
  }
}

@SuppressWarnings( "all" )
class StringExamples {
  public static void main( String[] args ) {

    // char
    char c1 = 'A';
    char c2 = 65;                           // ASCII-Wert für 'A'
    // char Operationen
    char nextChar = (char) (c1 + 1);        // 'B'
    // Character (Wrapper-Klasse für char)
    Character ch = new Character( 'A' );
    Character ch2 = 'A';                    // Autoboxing
    // Character statische Methoden
    boolean isDigit = Character.isDigit( '5' );       // true
    boolean isLetter = Character.isLetter( 'A' );     // true
    boolean isWhitespace = Character.isWhitespace( ' ' );  // true
    char upperCase = Character.toUpperCase( 'a' );    // 'A'
    char lowerCase = Character.toLowerCase( 'A' );    // 'a'

    // String
    String s1 = "tutego";
    String s2 = new String( "tutego" );     // Möglich, aber
    s1.length();                            // Länge des Strings
    s1.charAt( 0 );                         // Zeichen an Position 0
    s1.substring( 1, 4 );                   // Teilstring von Index 1 bis 3
    s1.toLowerCase();                       // In Kleinbuchstaben
    s1.toUpperCase();                       // In Großbuchstaben
    s1.trim();                              // Leerzeichen am Anfang und Ende entfernen
    s1.replace( 'e', 'a' );                 // 'e' durch 'a' ersetzen
    s1.contains( "te" );                    // Prüft, ob "te" enthalten ist
    String[] parts = s1.split( "e" );       // Teilt String an 'e'

    // String Vergleiche
    boolean isEqual = s1.equals( s2 );      // Inhalt vergleichen
    boolean isSameRef = (s1 == s2);         // Referenz vergleichen (Vorsicht!)
    int compResult = s1.compareTo( s2 );    // Lexikografischer Vergleich, <0, ==0, >0

    // StringBuilder
    StringBuilder sb = new StringBuilder();
    StringBuilder sb2 = new StringBuilder( "Initial content" );
    sb.append( "Hello" );                   // Anhängen
    sb.insert( 5, " World" );               // Einfügen an Position 5
    sb.delete( 5, 11 );                     // Löschen von Index 5 bis 10
    sb.reverse();                           // Umkehren
    String result = sb.toString();          // In String umwandeln

    // Konvertierungen
    String str = "Hello";
    char[] charArray = str.toCharArray();           // String zu char-Array
    char[] charArray2 = { 'W', 'o', 'r', 'l', 'd' };
    String str2 = new String( charArray2 );           // char-Array zu String
    int num = 123;
    String numStr = String.valueOf( num );            // int zu String
    // oder
    String numStr2 = Integer.toString( num );
    String numStr3 = "456";
    int parsedNum = Integer.parseInt( numStr3 );      // String zu int
  }
}

@SuppressWarnings( "all" )
class CoreClasseExamples {
  public static void main( String[] args ) {
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

@SuppressWarnings( "all" )
// Basisklasse für geometrische Formen
abstract class Shape {
  //  ☝️                               Von abstrakten Klassen können keine Instanzen gebildet werden.
  private String color;
  //  ☝️                               Private Eigenschaft ist außerhalb von Shape nicht einsehbar.

  Shape( String color ) {            // Parametrisierter Konstruktor
    this.color = color;              // Initialisiert die Farbe
  }

  public String getColor() {
    return /*this.*/color;
    //        ☝️                     this ist nicht nötig, da es keinen Namenskonflikt gibt.
  }

  public abstract double getArea();
  //        ☝️  Eine abstrakte Methode muss von allen Unterklassen implementiert werden,
  //           oder die Unterklasse muss selbst abstrakt sein.

  // Konkrete Methode in der abstrakten Klasse
  public void displayInfo() {
    System.out.println( "Dies ist eine " + getColor() + " Form." );
    //                                       ☝️  Auch direkter Zugriff auf color wäre denkbar.
  }
}

@SuppressWarnings( "all" )
class Rectangle extends Shape {
  //             ☝️                     Rectangle erbt von Shape. Nur eine Oberklasse ist erlaubt.
  private double width;
  private double height;

  // Konstruktor
  public Rectangle( String color, double width, double height ) {
    super( color );
    // ☝️                                Mit super Aufruf des Konstruktors der Oberklasse.
    this.width = width;
    this.height = height;
  }

  // Getter und Setter
  public double getWidth() {return width;}

  public void setWidth( double width ) {this.width = width;}

  public double getHeight() {return height;}

  public void setHeight( double height ) {this.height = height;}

  // Implementation der abstrakten Methode
  @Override
  // ☝️                     Annotation dokumentiert das Überschreiben von Methoden.
  public double getArea() {
    return width * height;
  }

  // Rectangle kann als Unterklasse neue Methode hinzufügen.
  public double getPerimeter() {
    return 2 * (width + height);
  }

  // Überschreiben der Methode displayInfo()
  // Alle nicht-privaten und nicht-finalen Methoden können überschrieben werden.
  @Override
  public void displayInfo() {
    super.displayInfo();
    System.out.println( "Es ist ein Rechteck mit Breite " + width + " und Höhe " + height + "." );
  }

  // Statische Methode zum Vergleich zweier Rechtecke
  public static Rectangle getLarger( Rectangle r1, Rectangle r2 ) {
    return r1.getArea() > r2.getArea() ? r1 : r2;
  }
}

@SuppressWarnings( "all" )
class RectangleExamples /* extends Object */ {
  //                          ☝️    Wird keine explizite Oberklasse erweitert, ist es automatisch Object.

  public static void main( String[] args ) {
    Rectangle rect1 = new Rectangle( "Rot", 5, 3 );
    Rectangle rect2 = new Rectangle( "Blau", 4, 4 );

    System.out.println( "Rechteck 1:" );
    rect1.displayInfo();
    System.out.println( "Fläche: " + rect1.getArea() );
    System.out.println( "Umfang: " + rect1.getPerimeter() );

    System.out.println( "\nRechteck 2:" );
    rect2.displayInfo();
    System.out.println( "Fläche: " + rect2.getArea() );
    System.out.println( "Umfang: " + rect2.getPerimeter() );

    Shape shape1 = new Rectangle( "Rot", 5, 3 );
    Shape shape2 = new Rectangle( "Blau", 4, 2 );
    // ☝️   Referenztyp kann ein Basistyp sein
    //                  ☝️   Objekttyp

    Shape[] shapes = { shape1, shape2, new Rectangle( "Grün", 2, 2 ) };

    for ( Shape shape : shapes ) {
      shape.displayInfo();
      System.out.println( shape.getArea() );
      //                          ☝️   Methodenaufruf dynamisch gebunden an tatsächlichen Typ (Polymorphie)

      if ( shape instanceof Rectangle ) {
        //          ☝️                       Prüfen, ob hinter shape etwas vom Typ Rectangle steht.
        Rectangle rect = (Rectangle) shape;
        System.out.println( rect.getPerimeter() );
        //                           ☝️     Ohne Typumwandlung gibt es getPerimeter() auf Shape nicht.
      }
    }

    if ( shape1 instanceof Rectangle rectangle1 && shape2 instanceof Rectangle rectangle2 ) {
      //                             ☝️   Pattern-Variable bei instanceof
      //                                                                       ☝️
      Rectangle larger = Rectangle.getLarger( rectangle1, rectangle2 );
    }
  }
}
```
