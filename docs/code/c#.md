C# PlayGround | C# Online Compiler | .NET Fiddle
https://dotnetfiddle.net/srx9kM

prog1
double wert = 3.5;
		double gerundet = Math.Round(wert);
		Console.WriteLine("Math.Round " + gerundet);
		double gerundetkfm = Math.Round(wert,2);
		Console.WriteLine("Math.Round mit 2 Kommastellen " + gerundetkfm);
		double gerundetkfm2 = Math.Round(wert,2, MidpointRounding.AwayFromZero);
		Console.WriteLine("Math.Round mit 2 Kommastellen (weg von der Null) " + gerundetkfm2);

prog2
using System;
 
public class Program
{
	public static void Main()
	{
		Console.Write("Vorname:  ");
		string vorname = Console.ReadLine();
		Console.Write("Nachname: ");
		string nachname = Console.ReadLine();
		Console.Write("Alter:    ");
		double alter  = Convert.ToDouble(Console.ReadLine());
		Console.Write("Lieblingsprogrammiersprache: ");
		string Lieblingsprogramiersprache = Console.ReadLine();
		Console.WriteLine("Ich heisse " + vorname + " " + nachname + ". Bin " + alter +" Jahre und programmiere gern mit " + Lieblingsprogramiersprache);	
	}
}

prog3
using System;

public class Program

{

	public static void Main()

	{

		        // Eingabeaufforderung der Daten

        Console.Write("Bitte gib deinen Namen ein: ");

        string Name = Console.ReadLine();
 
        Console.Write("Bitte gib deinen Ausbildungsberuf ein: ");

        string Beruf = Console.ReadLine();

				// Ausgabe als Satz

        Console.WriteLine();

        Console.WriteLine($"Hallo {Name}, dein Beruf ist {Beruf}.");
 
	}

}
 
prog4
using System;
public class Program
{
	public static void Main()
	{
		Console.WriteLine("Hallo Du, da.");

 
        Console.Write("Bitte gib deinen Namen ein: ");
        string name = Console.ReadLine(); // Eingabe lesen
        Console.WriteLine("Hallo " + name + " und was hast du mal gelernt!"); // Ausgabe
		string beruf = Console.ReadLine(); // Eingabe lesen
		Console.WriteLine("Hallo " + name + " dein Beruf ist " + beruf + " , das ist ja wirklich sehr interessant"); // Ausgabe
		Console.WriteLine($"Hallo {name} dein Beruf ist {beruf } , das ist ja wirklich sehr interessant"); // Ausgabe
    }
}

prog5
Beispiel für Logische Auswertungen
 
using System;

public class Program

{

	public static void Main()

	{

		bool wert1 = false;

		bool wert2 = true;

		Console.WriteLine("UND: " + (wert1 && wert2));

		Console.WriteLine("Oder: " + (wert1 || wert2));

	}

}

prog6
using System;
public class Program
{
	public static void Main()
	{
		int quadratVon = Quadrat(8);
		Console.WriteLine(quadratVon);
		Console.WriteLine(BerechneSteuerBetrag(quadratVon));
	}
	static int Quadrat(int x) 
	{
    	return x * x;
	}
	static double BerechneSteuerBetrag(double wert)
	{
		return wert * 0.19;
	}	
}

https://learn.microsoft.com/de-de/dotnet/csharp/methods

prog7
public static void Main()

	{

		Console.Write("Bitte Note eingeben (1-6):");

		int note = int.Parse(Console.ReadLine());	

		string notenBewertung = "";

		if (note >= 1 && note <= 6) // Eingabevalidierung

		{

			if (note == 1) notenBewertung = "sehr gut";

			if (note == 2) notenBewertung = "gut";

			if (note == 3) notenBewertung = "befriedigend";

			if (note == 4) notenBewertung = "ausreichend";

			if (note == 5) notenBewertung = "mangelhaft";

			if (note == 6) notenBewertung = "ungenügend";

		} else {

			Console.WriteLine("Falsche Eingabe!");

		}

		Console.WriteLine(" Die Note " + note + " wird als " + notenBewertung + " bewertet.");

	}
 
public static void Main()

	{

		const int ADD = 1;

		const int SUB = 2;

		const int MUL = 3;

				Console.Write("Bitte erste Zahl eingeben:");

		int zahl1 = int.Parse(Console.ReadLine());	

		Console.Write("Bitte zweite Zahl eingeben:");

		int zahl2 = int.Parse(Console.ReadLine());	

		Console.Write("Welche Rechenoperation soll ausgeführt werden? (1:Add 2:Sub: 3: Mult)");

		int auswahl = Convert.ToInt32(Console.ReadLine());

		int ergebnis = 0;

		switch (auswahl) {

			case ADD: ergebnis = zahl1 + zahl2; break;

			case SUB: ergebnis = zahl1 - zahl2; break;

			case MUL: ergebnis = zahl1 * zahl2; break;

			default: Console.WriteLine("Operationsauswahl ungültig!"); break;	

		}

		Console.WriteLine(" Das Ergebnis ist " + ergebnis );

	}
 
Random zufall = new Random();

		int zahl = zufall.Next(1, 10);

		Console.WriteLine("Zufallszahl: " + zahl);


prog8

Vergleich der Laufzeit für die Summe von n Zahlen iterativ/rekursiv
 
using System;

using System.Diagnostics;

public class Program

{

	static int berechneIterativ(int n) 

{

	int summe = 0;

	for (int i = 1; i <= n; i++)

	{

		summe += i; // summe = summe + i;

	}

	return summe;

}

static int berechneRekursiv(int n)

{

   // Abbruchbedingung

   if (n == 1)

       return 1;

   // Rekursiver Aufruf

   return n + berechneRekursiv(n - 1);

}
 
 
	public static void Main()

	{

		int zahlBis = 10000;

		Stopwatch sw = new Stopwatch();

		sw.Start();

		Console.WriteLine(berechneIterativ(zahlBis));

		sw.Stop();

		Console.WriteLine("Die iterative Berechnung hat " + sw.ElapsedTicks/100 + " ns benötigt" );

		sw.Start();

		Console.WriteLine(berechneRekursiv(zahlBis));

		sw.Stop();

		Console.WriteLine("Die rekursive Berechnung hat " + sw.ElapsedTicks/100 + " ns benötigt" );

	}

}
 
Zwischen zwei Messungen mit der Stopwatch-Klasse muss  Reset() aufgerufen werden.
 
 prog9
 using System;
using System.Globalization;
 
class Program 
{
	static void  Main()
	{
		// Übung 1
		Console.WriteLine("Übung 1");
		// Geburtsdatum eingeben
        // Console.WriteLine("Gib dein Geburtsdatum ein (yyyy-MM-dd): ");
		// Eingabe schon mal vorweggenommen :-)
        string eingabe = "1973-12-29"; //Console.ReadLine();
		Console.WriteLine("Gib dein Geburtsdatum ein (yyyy-MM-dd): " + eingabe);
		DateTime geburt = DateTime.Parse(eingabe);
		DateTime heute = DateTime.Today;
		// Tage seit der Geburt
        TimeSpan seitGeburt = heute - geburt;
		Console.WriteLine(seitGeburt.Days);
		//  Nächster Geburtstag
        int aktuellesJahr = heute.Year;
        DateTime naechsterGeburtstag = new DateTime(aktuellesJahr, geburt.Month, geburt.Day);
		// Wenn der Geburtstag dieses Jahr schon vorbei ist, nächstes Jahr nehmen ein Jahr drauf rechnen
        if (naechsterGeburtstag < heute)
        {
            naechsterGeburtstag = naechsterGeburtstag.AddYears(1);
        }
        TimeSpan bisGeburtstag = naechsterGeburtstag - heute;
        Console.WriteLine($"Bis zum nächsten Geburtstag: {bisGeburtstag.Days} Tage.");
		// Übung 2
		Console.WriteLine("");
		Console.WriteLine("Übung 2");
		DateTime jetzt = DateTime.Now;
 
        // Datum im Format TT.MM.JJJJ
        string datum = jetzt.ToString("dd.MM.yyyy");
        Console.WriteLine($"Heute: {datum}");
 
        // Wochentag ausgeschrieben (Deutsch)
        string wochentag = jetzt.ToString("dddd", new CultureInfo("de-DE"));
        Console.WriteLine($"Wochentag: {wochentag}");
 
        // Uhrzeit im Format HH:mm
        string uhrzeit = jetzt.ToString("HH:mm");
        Console.WriteLine($"Aktuelle Uhrzeit: {uhrzeit}");
		// Übung 3
		Console.WriteLine("");
		Console.WriteLine("Übung 3");
		// Arbeitsbeginn und Arbeitsende festlegen
        TimeSpan arbeitsbeginn = new TimeSpan(8, 15, 0);   // 08:15
        TimeSpan arbeitsende   = new TimeSpan(16, 52, 0);  // 16:52
 
        // Dauer berechnen
        TimeSpan dauer = arbeitsende - arbeitsbeginn;
 
        // hh:mm Ausgabe
        Console.WriteLine($"Arbeitszeit (hh:mm): {dauer.Hours:D2}:{dauer.Minutes:D2}");
 
        // Industriezeit (Stunden als Dezimalzahl)
        double industrieZeit = dauer.TotalHours;
        Console.WriteLine($"Arbeitszeit (Industriezeit): {industrieZeit:F2} Stunden");
	}
}

prog10

/*
Abschlussübung: Multiple-Choice-Quiz in C# mit Dateiein- und -ausgabe

Die Lernenden entwickeln ein Konsolenprogramm in zwei Schritten:

Nutzung von Datenstrukturen im Quelltext (hier kann man den Editor unter https://dotnetfiddle.net/ nutzen.)
Definition einer Datenstruktur innerhalb eines Strings mit einem zu definierenden Trennzeichen z.B. Semikolon
Fragetext
Option A bis Option D
Der richtigen Antwort als Buchstabe
In einer eigenen Methode die einzelnen Bestandteile aus einem string einliest mit z.B. string.Split(';');
Tipp: Für den Zugriff auf die einzelnen Komponenten im Array kann man sich Konstanten definieren (z.B. FRAGE = 0 bzw. ANTWORT=5). Alternativ kann auch eine Enumeration verwendet werden.
Jede Frage mit vier Antwortmöglichkeiten (A–D) (Mithilfe einer Schleife) präsentiert
Optional die Fragen in zufälliger Reihenfolge (Mit Hilfe der Random-Klasse) abfragt
Die Eingabe des Nutzers auswertet
Optional ohne Beachtung der Groß-/Kleinschreibung durch Nutzung von String.ToUpper()
Am Ende die Anzahl der richtigen Antworten und den Prozentsatz berechnet
Eine Ausgabe bestanden bei mindestens 50% richtiger Antworten ausgibt.
*/
using System;

class Quiz
{
    /**
        Aufgabenteil: 2. siehe unten

        Status: implementieren

        Nutzung: Soll Frage bekommen in Format "Frage;OptionA;OptionB;OptionC;OptionD;richtigeOption"
        
        Aufgabe: Trennt an Trennzeichen auf 
        
        Liefert zurück:

            return[0] Fragetext
            return[1] Option A
            ...
            return[5] richtige Antwort als "Buchstabe"
    **/
    static string[] fragenParsen(string zeile)
    {
        string[] teile = new string[5];

        return teile;
    }


    /**
        Aufgabenteil: 3. Präsentation einer Frage

        Status: implementieren

        Nutzung: von `fragenParsen` gelieferter Wert als Eingabe-/Aufruf-Parameter
        
        Aufgabe: Schön für Benutzer präsentieren

            Auf Konsole, erst Frage, dann Antwortmöglichkeiten

        Zusatzaufgabe (optional): Optionen/Antwortmöglichkeiten in zufälliger Reihenfolge
        
        Liefert zurück: nix
    **/
    static void fragePräsentieren(string[] GEPARSTE_FRAGE)
    {
        string FRAGE_AUS_ZEILE = GEPARSTE_FRAGE[0];
        string RICHTIGE_ANTWORT = GEPARSTE_FRAGE[4];

        Console.WriteLine($"Frage: {FRAGE_AUS_ZEILE}");
    }


    /**
        Aufgabenteil: 4. 

        Status: implementieren

        Nutzung: selbst gewählte Aufrufart nutzen
        
        Aufgabe: Vergleiche/Auswerten

            Prüfung ob Eingabe gültig(!)

        Liefert zurück: vielleicht
    **/
    static void benutzerauswahlAuswerten(string[] A)
    {
        
    }
    static void benutzerauswahlAuswerten(string A)
    {
        
    }

    static void Main()
    {

        /**
            Aufgabenteil: 1.
            
            Status: verbesserungsfähig: bessere Fragen wählen

            Aufgabe: Datenstrukture zur Speicherung von Strings. Jeder String eine Frage:
             - mit einem zu definierenden Trennzeichen
             - Trennzeichen (TRENNER) trennt: 
                  - Fragetext
                  - Option A bis Option D
                  - Der richtigen Antwort als Buchstabe
            **/
        const string TRENNER = ";";

        string[] fragen = {
            // Fragetext                     Trenn Option A   Option B    Option C Option D
            "In welchem Land spricht man Spanisch?;Frankreich;Deutschland;Portugal;Spanien;D",
            "Anderes Wort für Mensch?             ;Homo Sapiens;Homo Erectus;Homo Domo;Hase;A",
            "Frage"+TRENNER
            + "Antwort A"+TRENNER
            + "Antwort B"+TRENNER
            + "Antwort C"+TRENNER
            + "Antwort D"+TRENNER
            + "C"
        };

        // Hauptschleife/Dauer-Programmlogik
        // bis Quiz zuende
        for (int i = 0; i < fragen.Length; ++i)
        {
            // 2. eigenen Methode die einzelnen Bestandteile aus string erhalten. z.B. Trennzeichen
            // liefert string array, Frage, Optionen, richtige Antwort
            var GEPARSTE_FRAGE = fragenParsen(fragen[i]);

            // 3. jede Frage mit Antwortmöglichkeiten (Mithilfe einer Schleife) "präsentieren"
            // 3.1 Optional(!) die Fragen in zufälliger Reihenfolge (Mit Hilfe der Random-Klasse) abfragt
            fragePräsentieren(GEPARSTE_FRAGE);

            // 4. Eingabe des Nutzers auswerten:
            // 4.1 Optional ohne Beachtung der Groß-/Kleinschreibung
            // ToDo: eine der beiden Möglichkeiten implementieren
            benutzerauswahlAuswerten(GEPARSTE_FRAGE); // Möglichkeit A: richtiges Ergebnis finden, Benutzer wählt zwischen A und D; Vergleich auf Richtigkeit
            benutzerauswahlAuswerten(GEPARSTE_FRAGE[5]); // Möglichkeit B: Benutzer wählt zwischen A und D; Vergleich auf Richtigkeit
        }
        // Quiz Ende
        // 5. Anzahl der richtigen Antworten und den Prozentsatz berechnen
        // ToDo: direkt hier oder auch als Funktion. Eure Wahl.

        // 6. Ausgabe "bestanden" bei mindestens 50% richtiger Antworten
        // ToDo: direkt hier oder auch als Funktion. Eure Wahl.

    }
}
