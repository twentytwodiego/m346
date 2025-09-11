## Webseite
![FunktionierendeWebsite](/Bilder/working_website.png)

## Öffentliche IP
![OeffentlicheIP](/Bilder/instance_withpubip.png)

## Regeln Sicherheitsgruppe
![Rules](/Bilder/rulesofinstance.png)

## Login mysql Konsole
![mysqlKonsole](/Bilder/mysql_login.png)

## SQL-Abfrage

Mit der Abfrage  
```sql
SELECT Host, User FROM mysql.user;
```

werden alle in der Datenbank vorhandenen Benutzer angezeigt.

Die Spalte User zeigt den Benutzernamen des Datenbankkontos (z. B. `root`, `admin`, `mysql`).
Die Spalte Host zeigt an, von welchem Rechner oder Netzwerk sich dieser Benutzer anmelden darf.

* `localhost` bedeutet, der Benutzer darf sich nur vom Server selbst verbinden
* `%` bedeutet, der Benutzer kann sich von überall her anmelden

Im Resultat sehe ich z. B. meinen selbst erstellten Benutzer **`admin`@`%`**, der von allen Hosts erreichbar ist. Ausserdem erscheinen noch Systembenutzer wie `root@localhost`, `mysql@localhost` und `mariadb.sys@localhost`.

Damit kann ich überprüfen, dass mein Benutzer korrekt erstellt wurde und von außen erreichbar ist.

![mySQLCommand](/Bilder/select_abfrage.png)