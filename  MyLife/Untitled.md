
Sehr gute Idee! Genau so eine „Utility-Klasse“ (z. B. Utils oder Jute) ist in Java üblich, wenn man sich die kleinen Helferlein aus anderen Sprachen nachbauen möchte. Damit kannst du dir die Funktionen, die dir in BlueJ/Java fehlen, selbst bereitstellen. Hier ein paar konkrete Vorschläge, die dich an TypeScript erinnern werden und im Alltag nützlich sind:

---

Mögliche Funktionen für deine `Jute`-Klasse

1. Array-Suche• findIndex(int[] arr, int value): Gibt den Index des ersten Vorkommens zurück, oder -1 wenn nicht gefunden.
• contains(int[] arr, int value): Gibt true zurück, wenn der Wert im Array vorkommt.

2. String-Helfer• isEmpty(String s): Prüft, ob ein String leer oder null ist.
• reverse(String s): Dreht den String um.
• capitalize(String s): Macht den ersten Buchstaben groß.

3. Mathematische Utilities• clamp(int value, int min, int max): Begrenze einen Wert auf einen Bereich.
• sum(int[] arr): Summiert alle Werte im Array.
• average(int[] arr): Gibt den Durchschnitt zurück.

4. Collections• unique(int[] arr): Entfernt Duplikate aus einem Array.
• merge(int[] arr1, int[] arr2): Führt zwei Arrays zusammen.
• max(int[] arr), min(int[] arr): Gibt den größten/kleinsten Wert zurück.

5. Generische Hilfen• repeat(String s, int times): Wiederholt einen String mehrfach.
• join(String[] arr, String delimiter): Verbindet ein Array zu einem String mit Trennzeichen.
• range(int start, int end): Erzeugt ein Array von Zahlen zwischen Start und Ende.



---

Beispiel: `findIndex` in Java

public class Jute {
    public static int findIndex(int[] arr, int value) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == value) {
                return i;
            }
        }
        return -1; // nicht gefunden
    }
}


Beispiel: `clamp`

public static int clamp(int value, int min, int max) {
    if (value < min) return min;
    if (value > max) return max;
    return value;
}

public class Jute {

    // 1. Array-Suche
    public static int findIndex(int[] arr, int value) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == value) return i;
        }
        return -1;
    }

    public static boolean contains(int[] arr, int value) {
        return findIndex(arr, value) != -1;
    }

    // 2. String-Helfer
    public static boolean isEmpty(String s) {
        return s == null || s.length() == 0;
    }

    public static String reverse(String s) {
        return new StringBuilder(s).reverse().toString();
    }

    public static String capitalize(String s) {
        if (isEmpty(s)) return s;
        return s.substring(0,1).toUpperCase() + s.substring(1);
    }

    // 3. Mathematische Utilities
    public static int clamp(int value, int min, int max) {
        if (value < min) return min;
        if (value > max) return max;
        return value;
    }

    public static int sum(int[] arr) {
        int total = 0;
        for (int v : arr) total += v;
        return total;
    }

    public static double average(int[] arr) {
        if (arr.length == 0) return 0;
        return (double) sum(arr) / arr.length;
    }

    // 4. Collections
    public static int max(int[] arr) {
        int m = arr[0];
        for (int v : arr) if (v > m) m = v;
        return m;
    }

    public static int min(int[] arr) {
        int m = arr[0];
        for (int v : arr) if (v < m) m = v;
        return m;
    }

    public static int[] merge(int[] arr1, int[] arr2) {
        int[] merged = new int[arr1.length + arr2.length];
        System.arraycopy(arr1, 0, merged, 0, arr1.length);
        System.arraycopy(arr2, 0, merged, arr1.length, arr2.length);
        return merged;
    }

    public static int[] unique(int[] arr) {
        java.util.Set<Integer> set = new java.util.HashSet<>();
        for (int v : arr) set.add(v);
        int[] result = new int[set.size()];
        int i = 0;
        for (int v : set) result[i++] = v;
        return result;
    }

    // 5. Generische Hilfen
    public static String repeat(String s, int times) {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < times; i++) sb.append(s);
        return sb.toString();
    }

    public static String join(String[] arr, String delimiter) {
        return String.join(delimiter, arr);
    }

    public static int[] range(int start, int end) {
        int[] result = new int[end - start + 1];
        for (int i = 0; i < result.length; i++) {
            result[i] = start + i;
        }
        return result;
    }
}

---

Tipp für dich

• Fang mit einfachen Array- und String-Funktionen an, weil du die sofort im Unterricht einsetzen kannst.
• Bau die Klasse modular auf, sodass du später jederzeit neue Methoden hinzufügen kannst.
• Orientiere dich ruhig an den JavaScript/TypeScript-Array-Methoden (map, filter, reduce) und überlege, wie du sie in Java nachbauen würdest.


---

Willst du, dass ich dir eine erste kleine Sammlung von 5–6 fertigen Methoden direkt als komplette Jute-Klasse schreibe, damit du sofort loslegen kannst?


Sehr gute und wichtige Frage – lass uns das Schritt für Schritt auseinandernehmen:

---

1. Gibt es `filter` in Java?

• Direkt auf Arrays: Nein, Arrays in Java haben keine Methoden wie .filter() oder .map() wie in JavaScript/TypeScript.
• Aber: Seit Java 8 gibt es Streams, und die haben genau solche Methoden.
Beispiel:int[] arr = {1, 2, 3, 4, 5};

// Filter: nur gerade Zahlen
int[] even = java.util.Arrays.stream(arr)
                             .filter(x -> x % 2 == 0)
                             .toArray();

System.out.println(java.util.Arrays.toString(even)); 
// Ausgabe: [2, 4]



---

2. Gibt es `some` in Java?

• In JavaScript: arr.some(x => x > 10) prüft, ob irgendein Element die Bedingung erfüllt.
• In Java mit Streams:int[] arr = {1, 2, 3, 4, 5};

boolean hasBig = java.util.Arrays.stream(arr)
                                 .anyMatch(x -> x > 3);

System.out.println(hasBig); 
// Ausgabe: true

• Ähnlich gibt es auch allMatch (alle erfüllen Bedingung) und noneMatch (keiner erfüllt Bedingung).


---

3. Gibt es Lambdas in Java?

• Ja, seit Java 8.
• Syntax: (Parameter) -> Ausdruck oder (Parameter) -> { Block }.
• Beispiel:java.util.List<String> names = java.util.Arrays.asList("Anna", "Bernd", "Clara");

// Filter mit Lambda
names.stream()
     .filter(name -> name.startsWith("A"))
     .forEach(System.out::println);

// Ausgabe: Anna



---

4. Vergleich mit TypeScript

TypeScript:

let arr = [1, 2, 3, 4, 5];
let evens = arr.filter(x => x % 2 === 0);
let hasBig = arr.some(x => x > 3);


Java (Streams + Lambdas):

int[] arr = {1, 2, 3, 4, 5};
int[] evens = java.util.Arrays.stream(arr)
                              .filter(x -> x % 2 == 0)
                              .toArray();
boolean hasBig = java.util.Arrays.stream(arr)
                                 .anyMatch(x -> x > 3);


---

Fazit

• Arrays in Java selbst sind sehr simpel und haben keine filter/map/some.
• Mit Streams und Lambdas kannst du aber fast identisch arbeiten wie in TypeScript.
• Seit Java 8 ist das Standard und wird überall genutzt.


---

Willst du, dass ich dir eine Mini-Übersichtstabelle baue: „TypeScript-Array-Methode → Java-Stream-Äquivalent“, damit du sofort siehst, wie du deine Lieblingsfunktionen übertragen kannst?


int[] arr = {1, 2, 3, 4, 5};

// Array → Stream → Filter → zurück zu Array
int[] even = java.util.Arrays.stream(arr)   // Array in Stream verwandeln
                             .filter(x -> x % 2 == 0) // nur gerade Zahlen
                             .toArray();              // zurück zu int[]

System.out.println(java.util.Arrays.toString(even));
// Ausgabe: [2, 4]
