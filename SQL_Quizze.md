# Scenario
The database runs on the server PFSQL01, so you need to connect the server.
Du bist beauftragt, einem Datanbenkentwickler dabei zu helfen, Abfragen zu erstellen und seine parat erstellten Abfragen auf Richtigkeit zu prüfen

# Requirenments
-   Du bist innerhalb unseres LAN-Segments oder via VPN verbunden
-   Du hast Microsoft SQL Server Management Studio installiert

# Start
Verbinde dich mit dem PFSQL01 Server, wähle die datenbank Quiz_Database aus und eine neue Query Session. Diese Datenbank gehört einer Großhandelfirma und besteht aus 6 tabellen (Mitarbeiter, Kunde, Eindeut_plz, Artikel, Artikelgruppen, Auftragsposition)

# Tasks
## Stufe 1:
1. Zeige alle Informationen der Tabelle Mitarbeiter. Wie viele Mitarbieter beschäftigt die Firma?
2.  Sortiere die Kundendaten nach der Postleitzahl aufsteigend. Bei der gleichen Postleitzahl werden die Datensätze nach Kundenamen absteigend sortiert.
So soll das Ergebnis aussehen:
![Auf_2.png](./src/stg1_Auf_2.png)
3. Welcher Mitarbeiter der Steuerklasse III verdient mehr als 6000 €
4. Welche der folgenden Abfragen liefert folgenden Tabelle aus:
![Auf_4.png](./src/stg1_Auf_4.png)

    - SELECT Name, Vorname, Vorname + '.' + Name + '@großhandel.de' as E-Mail
    FROM Mitarbeiter
    - SELECT Name, Vorname, Vorname + '.' + Name + '@großhandel.de' as "E-Mail"
    FROM Mitarbeiter
    - SELECT Name, Vorname, Vorname + . + Name + @großhandel.de as E-Mail
    FROM Mitarbeiter
    - Keine
## Stufe 2:
1. Wie groß ist das Minimal- bzw. Maximalgehalt in der Firma?
2. Mit welcher der folgenden Skripte können Aufträge, die im Jahr 1999 aufgenommen wurden abgefragt?

    - SELECT count(*) AS [Aufträge Anzahl]
    FROM Auftrag
    HAVING YEAR(Auftragsdatum) = 1999;
    - SELECT count(Auftragsnummer) AS [Aufträge Anzahl]
    FROM Auftrag
    HAVING YEAR(Auftragsdatum) = 1999;
    - SELECT count(*) AS [Aufträge Anzahl]
    FROM Auftrag
    WHERE YEAR(Auftragsdatum) = 1999;
    - SELECT count(Auftragsdatum)
    FROM Auftrag
    WHERE YEAR(Auftragsdatum) = 1999;
3. Eine der folgenden Abfragen liefert folgendes Ergebnis zurück:
![stg2_Auf3.png](./src/stg2_Auf3.png)
    - SELECT Abteilung, avg(Gehalt) "durchschnt. Gehalt" FROM MITARBEITER;
    - SELECT Abteilung, avg(Gehalt) "durchschnt. Gehalt" FROM MITARBEITER
    GROUP BY Gehalt;
    - SELECT Abteilung, avg(Gehalt) durchschnt. Gehalt FROM MITARBEITER
    GROUP BY Abteilung;
    - SELECT Abteilung, avg(Gehalt) "durchschnt. Gehalt" FROM MITARBEITER
    GROUP BY Abteilung;
4. Welche Steurklassen kommen in der Mitarbeiter Tabelle mehr als 4 Mal vor?
## Stufe 3:
1. Welche Artikel gehören zur Artikelgruppe mit der Bezeichnung „Peripherie“?
2. Mit welcher der Abfragen bekommst du das abgebildete Ergebnis?
![stg3_Auf2.png](./src/stg3_Auf2.png)
    - SELECT m.Vorname, m.Name, ep.Ort FROM MITARBEITER m
    RIGHT JOIN EINDEUT_PLZ ep ON ep.PLZ = m.Plz
    - SELECT m.Vorname, m.Name, ep.Ort FROM MITARBEITER m
    JOIN EINDEUT_PLZ ep ON ep.PLZ = m.Plz
    - SELECT m.Vorname, m.Name, ep.Ort FROM EINDEUT_PLZ ep
    LEFT JOIN MITARBEITER m ON ep.PLZ = m.Plz
    - SELECT m.Vorname, m.Name, ep.Ort FROM EINDEUT_PLZ ep
    RIGHT JOIN MITARBEITER m ON ep.PLZ = m.Plz
3. In Welchen Orten Wohnen sowohl Kunde als auch Mitarbeiter?
4. Folgende Abbildung zeigt Kunden an, die noch nicht etwas bestellt haben.
![stg3_Auf4.png](./src/stg3_Auf4.png)
Wie lautet die Abfrage für diese Tabelle?

# Autor
Name: Ali Ahmad

E-Mail: ali.ahmad@smenso.de