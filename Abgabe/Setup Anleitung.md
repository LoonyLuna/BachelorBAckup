Setup Anleitung:

Um ein Drupal 8 Instanz aufzusetzen sind folgende Dinge nötig:
- Kommadozeile (z. B. Bash, iTerm)
- Einen lokalen Web server (z. B. Apache, NGINX)
- Eine Datenbank (z.B. MySQL, MariaBD)
- Git
- Composer
- Drush

Das Einrichtungsbeispiel erfolgt anhand von NGINX in Verbidnung mit MariaDB auf einem MacBook. Alle in Großbuchtaben geschriebeen Wörter, müssen ersetzt werden mit den jeweiligen personalisierten Daten des Aufsetzenden.

Datenbank einrichten:
1. Kommandozeile öffnen und Datenbank ansprechen (mysql)
2. Datenbank erstellen (create database barrierefreiheit;)
3. Datenbanknutzer erstellen (create user 'barrierefreiheit'@'barrierefreiheit' identified by 'barrierefreiheit';)
4. Rechte zuweisen (grant all privileges on barrierefreiheit.* to 'barrierefreiheit'@'barrierefreiheit';)
5. exit

Web Server modifizieren:
1. Kommandozeile öffnen und in /etc spirngen (cd /etc)
2. Hosts bearbeiten (vim hosts)
3. Eintrag tätigen nachdem man 'i' gedrückt hat (127.0.0.1 barrierefreiheit.local)
4. Bestätigen (:x)
5. In Web Server Ordner springen (z. B. /etc/nginx/sites-enabled)
6. Server einrichten (z. B. server_name barrierefreiheit.local;
                            root /Users/BENUTZERNAME/sites/workspace/barrierefreiheit/web;
                            CUSTOM EINRICHTUNG FÜR SERVER)
7. Web Server neu starten (z. B. brew services restart nginx)

Drupal einrichten:
1. Kommandozeile öffnen und zu Zielort der Installation navigieren (z. B. Users/USERNAME/sites/workspace)
2. Drupal 8 Bachelor Beispiel klonen (git clone git@github.com:LoonyLuna/barrierefreiheit.git)
3. Dependencies installieren (composer install)
4. Drupal installieren (drush si standard --db-url=mysql://barrierefreiheit:barrierefreiheit@localhost/barrierefreiheit)
5. Dump in root Verzeichnis des Projektes packen
6. Ins web verzeichnis wechseln (cd web)
7. Per Drush Dump einspielen (../vendor/bin/drush drush sql:drop && drush sql:cli < ../DUMPNAME)
8. Lokale Webseite aufrufen im Broweser (barrierefreiheit.local aufrufen)