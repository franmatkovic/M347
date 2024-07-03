# KN02-Dockerfile

### A. Dockerfile I

1. Dokumentiertes Dockerfile

   `FROM nginx` Basisimage für den Webserver, in diesem Fall nginx <br>
   `COPY static-html-directory /var/www/html` Kopiert den Inhalt des Verzeichnisses static-html-directory in das Verzeichnis /var/www/html im Container <br>
   `EXPOSE 80` Legt fest, dass der Container Port 80 nach aussen freigibt, um den Webserver zu erreichen <br>

2. Dockerfile, welches mit den entsprechenden Zeilen wie oben beschrieben:
   [Dockerfile](/kn02/A/dockerfile)

3. Notwendige Docker-Befehle für das build: <br>
   `docker build -t fran686/m347:kn02a .`

4. Befehl für den Start des Containers:<br>
   `docker run -d -p 8080:80 fran686/m347:kn02a` <br>

5. Befehle für dem push in das private Repository: <br>
   `docker login`, <br>
   `docker push fran686/m347:kn02a`

6. Screenshot aus Docker Desktop, welcher das Image kn02a zeigt:
   ![](/kn02/A/img/kn02-1.png) <br>

7. Screenshot der HTML-Seite, der die Seite helloworld.html zeigt, nachdem der Container gestartet wurde: <br>
   ![](/kn02/A/img/kn02-2.png) <br>

### B. Dockerfile II

1. DB: telnet Befehl der zeigt, dass der Zugriff auf den DB Server funktioniert (Screenshot):
   ![](/kn02/B/img/1.png) <br>

2. DB: Dockerfile für Ihren DB-Container: [Dockerfile](/kn02/B/dockerfile)

3. DB: docker build und docker run Befehle für Ihren DB-Container: <br>
   `docker build -t kn02b-db .` <br>
   `docker run -d --name kn02b-db -p 3306:3306 kn02b-db`

4. Web: Screenshots der beiden Seiten info.php und db.php:
   ![](/kn02/B/img/2.png) <br>
   ![](/kn02/B/img/3.png)

5. Web: Dockerfile für Ihren Web-Container:
   [Dockerfile](/kn02/B/dockerfile-web)

6. Web: docker build und docker run Befehle für Ihren Web-Container: <br>
   `docker build -t kn02b-web:latest -f dockerfile-web .` <br>
   `docker run -d --name kn02b-web -p 80:80 --link kn02b-db:db kn02b-web`

7. Web: Angepasste PHP-Dateien: <br>
   [info.php](/kn02/B/info.php) <br>
   [db.php](/kn02/B/db.php)
