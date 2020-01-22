# Häufige Fragen über das Instabot

### Wie installiere ich das Instabot?

Die Installation ist abhängig von deinem Betriebssystem. [Installation für Windows](Installation_on_Windows.md). [Installation für Unix] (Installation_on_Unix.md) (Linux, MacOS).

Alle erforderlichen Schritte, wie z.B. die Installation des Bots, werden durch die Eingabeaufforderung durchgeführt (das Terminal / CMD). Keine Angst davor - daran ist nichts kompliziert.

### Wie starte ich das Bot?

Zunächst musst du es installieren. Gehe hiernach in den Beispiel-Ordner und starte eines der Skripte mithilfe der Eingabeaufforderung, zum Beispiel:

``` python
python multi_script_CLI.py
```
Wenn das Skript weitere Parameter benötigt zum Starten (wie zum Beispiel Hashtags zum Liken), wird es dir im Terminal angezeigt. Im Falle von like_hashtags.py wäre das Output:

```
Usage: Pass hashtags to like
Example: python like_hashtags.py dog cat
```

Es wird sofort ersichtlich, wie mit dem Bot zu arbeiten ist. Wenn du beispielsweise die neuesten Inhalte mit dem Hashtag **#katze** oder **#hund** liken willst, dann:

``` python
python like_hashtags.py katze hund
```

### Wo muss ich meinen Usernamen und mein Passwort eingeben?

Das lässt sich nicht genauer spezifizieren: Das Bot selber wird dich hiernach fragen, wenn es das erste Mal gestartet wird. Deine Daten werden in einer Text-Datei secret.txt gespeichert und automatisch verwendet bei zukünftiger Benutzung. Du kannst
sie aber auch manuell eingeben durch:

``` python
bot.login(username=«mein_username», password=«mein_passwort»)
```

Hinzu kommt, dass du beim ersten Start deines Bots mehrere Accounts hinzufügen kannst. Für zukünftige Fälle kannst du dann auswählen, welche Accounts du nutzen willst.

### Wenn ich mein Passwort eingebe, wird es nicht angezeigt. Was tun?

Das Passwort wird nicht angezeigt, damit es nicht von anderen ausgesphät werden kann. Keine Sorge, es wird korrekt erfasst. Wenn du versehentlich ein falsches Passwort eingegeben hast, wird es beim nächsten Start automatisch erkannt und du wirst erneut nach einer Eingabe gefragt.

### Wenn ich die Login-Daten und mein Passwort für meinen Instagram-Account eingebe, wohin gehen die Daten? Sind die Daten für andere ersichtlich?

Die eingegebenen Daten werden lokal in deinem Computer in einer secret.txt Textfile gespeichert. Sie werden keinen unbefugten Dritten zur Verfügung gestellt.

### Wird mein Account gesperrt?

Keine Sorge! Das Instabot hat bestimmte Grenzen was die Anzahl der Abos / Likes / Kommentare pro Tag angeht sowie die Frequenz der Anfragen - zum Beispiel werden andere Seiten nicht zu hastig abonniert. Instabot hat seine eigenen Limitationen, um es sicher zu nutzen. Du kannst auch deine eigenen Werte verwenden, aber sei hierbei vorsichtig. 

### Ist es möglich, anderen schneller zu entfolgen? Ist es sicher, schneller zu agieren?

Es gibt Parameter für die Objekt-Klasse `instabot.Bot ()`. Wenn du den Code __milti_script_CLI__ exekutierst, öffnet sich ein Text-Editor mit einem vordefinierten Wert __unfollow_delay = 30__. Du kannst diesen Wert beliebig ändern. Analog hierzu kannst du mit anderen Parametern verfahren. Dies kann allerdings unsicher sein!

Wenn du beispielsweise 100 Leute pro Sekunde entfolgen willst, wirst du mit Sicherheit gesperrt. Die Bot-Grenzen sind abhängig vom Gründungsdatum und der Follow-Zahl deines Accounts. Die eingetragenen Werten sind _für die meisten_ sicher. Bislang wurde noch niemand gesperrt.

### Ich möchte, dass das Bot Accounts entfolgt, die mir nicht zurückfolgen

Für diese Aufgabe haben wir bereits ein Skript im Beispiel-Ordner: unfollow_non_followes.py. Öffne den Ordner und führe das Skript mittels Eingabeauffoderung durch.

``` python
python unfollow_non_followers.py
```

### I möchte, dass das Bot Beiträge liked, die ich selber ausgesucht habe

Auch das ist sehr einfach! Führe like_hashtags.py durch mithilfe der folgenden Zeile im Terminal:

``` python
python like_hashtags.py autos geld
```

### Zu viele Skripts! Gibt es ein Alles-in-einem-Skript? 

Den gibt es. Dank der Bemühungen unserer Community wurde ein sehr cooles Skript geschrieben. Du kannst es unter [multi_script_CLI.py](/examples/multi_script_CLI.py) finden. Es ist auf Englisch, aber sehr gut verfasst. Du solltest es wirklich ausprobieren!

### Wie kann ich das automatische Posten von Fotos bei Instagram einstellen?

Hierfür haben wir ein Skript in [examples](/examples/autopost). Weiter unten auf der Seite findest du eine Anleitung zur Konfiguration des automatischen Postings.

### AutoPost veröffentlicht lediglich ein Foto oder eine Beschreibung. Wie kann ich Hashtags hinzufügen?

Hashtags funktionieren genauso wie Beschreibungen - füge sie hier einfach hinzu!

### Kann ich Videos automatisch posten lassen?

Leider nicht. Das würde die Größe des Projektes dramatisch erhöhen.

### Wie kann ich bei diesem Projekt helfen?

Du kannst:
* einen Stern in Github hinzufügen. Um dies zu tun, klicke ganz einfach auf den Stern auf der Seite https://github.com/instagrambot (oben rechts). Du musst dich hierfür ggf. (gratis) registrieren.
* Log dich in die [Telegram Gruppe](https://t.me/instabotproject) ein und helfe Anfängern, die Installation und Konfiguration des Instabots zu verstehen!
* Teile uns deine Meinung über das Projekt mit anderen! Du kannst hierfür den folgenden Link teilen: https://instagrambot.github.io.
* Wenn du Fehler oder Bugs findest, teile uns das in [Probleme und Bugs](https://github.com/instagrambot/instabot/issues) mit. Stelle sicher, dass du _Screenshots_ und _Kommandos_ hinzufügst. Dies hilft uns, die Fehler zu korrigieren und das Instabot zu verbessern!
* Wenn du ein Entwickler bist, korrigiere die Fehler! Mach das mithilfe eines Pull Request gemäß den PEP8 Standards.
* Um unser Projekt weiterzuenwickeln: [Seite](https://github.com/instagrambot/instagrambot.github.io). Wir benötigen Web-Designer und Frontend-Entwickler. Wenn du schon immer etwas aus dem Nichts erstellen wolltest, bist du herzlich willkommen!
