# Tutorium - Grundlagen Datenbanken - Blatt 10

## Vorbereitung

* Für dieses Aufgabenblatt wird die SQL-Dump-Datei `Tutorium_Book.sql` benötigt, die sich in dem Verzeichnis `sql` befindet
* Die SQL-Dump Datei wird in SQL-PLUS mittels `start <Dateipfad> ` in Datenbank importieren
* Beispiele
  * Linux: `start ~/Tutorium_Book.sql`
  * Windows: `start C:\Users\max.mustermann\Desktop\Tutorium_Book.sql`

## Datenbankmodell
![Datenbankmodell](./img/Schema_mit_Beziehungen.png)

## Aufgaben

### Aufgabe 1
Erstelle einen Wait-For-Graphen für die untenstehende Tabelle. Liegt hier zum Zeitpunkt `t31` eine Deadlock-Situation vor? Falls ja, kennzeichne den Deadlock im Graphen.

Hilfestellung:
* Ein Shared Lock wird zum Lesen von Sätzen beantragt und verschiedene Transaktionen können sich diesen teilen.
* Ein Exclusive Lock wird z.B. zum Ändern von Datensätzen beantragt, kann nicht geteilt werden und kann nicht vergeben werden, wenn eine andere Transaktion einen Shared Lock auf den Satz besitzt.
* First come, first serve. Exclusive Locks, die zuerst angefordert wurden, werden zuerst bearbeitet.
* Am Ende der Transaktion (Commit/Rollback) werden alle Locks freigegeben
* Fetch(A): Shared-Lock wird für den Datensatz A angefordert.
*  Update(B): Exclusive-Lock wird für den Datensatz B angefordert.

| Zeitpunkt | Transaktion | Operation |
| --------- | ----------- | ----------|
| t0        | T1          | FETCH(A)  |
| t1        | T2          | FETCH(E)  |
| t2        | T3          | UPDATE(B) |
| t3        | T2          | FETCH(A)  |
| t4        | T4          | FETCH(B)  |
| t5        | T1          | UPDATE(F) |
| t6        | T5          | FETCH(A)  |
| t7        | T3          | FETCH(C)  |
| t8        | T1          | FETCH(G)  |
| t9        | T6          | UPDATE(G) |
| t10       | T7          | FETCH(A)  |
| t11       | T7          | FETCH(B)  |
| t12       | T3          | FETCH(D)  |
| t13       | T8          | FETCH(D)  |
| t14       | T5          | FETCH(C)  |
| t15       | T1          | COMMIT    |
| t16       | T3          | UPDATE(E) |
| t17       | T10         | FETCH(E)  |
| t18       | T2          | ROLLBACK  |
| t19       | T5          | UPDATE(D) |
| t20       | T7          | FETCH(F)  |
| t21       | T4          | UPDATE(F) |
| t22       | T4          | UPDATE(C) |
| t23       | T8          | FETCH(F)  |
| t24       | T3          | COMMIT    |
| t25       | T9          | FETCH(D)  |
| t26       | T8          | UPDATE(E) |
| t27       | T11         | UPDATE(G) |
| t28       | T5          | UPDATE(A) |
| t29       | T4          | UPDATE(B) |
| t30       | T6          | FETCH(A)  |
| T31       | T7          | COMMIT    |


### Aufgabe 2
Räume  dem Benutzer `SCOTT` das Recht ein, alle Einträge in der Tabelle `lib_book` anzusehen, neue Zeilen einzufügen, Zeilen zu löschen und nur den Titel ändern zu dürfen.

#### Lösung
```sql
Deine Lösung
```

### Aufgabe 3
Erstelle eine Namensliste, in der Vor- und Nachnamen aller Autoren und aller Kunden in einer Übersicht erfasst werden. Sortiere die Liste aufsteigend nach Nachnamen und innerhalb des Nachnamens absteigend nach dem Vornamen.

#### Lösung
```sql
Deine Lösung
```

### Aufgabe 4
Welche Bücher (`book_id`, `anzahlAusgeliehen`) wurden bisher am häufigsten ausgeliehen?

#### Lösung
```sql
Deine Lösung
```
