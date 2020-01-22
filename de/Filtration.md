# Wie filtert Instabot Leute aus?

Es ist kein Geheimnis, dass das Instabot Leute ausfiltert bevor er ihnen folgt. Weiter unten findest du eine komplette Liste an Bedingungen, die für den Filterprozess zutrage kommen.

## Optionen

Zunächst einmal sollte erwähnt werden, dass du alle Optionen selber verändern kannst. Nachfolgend findest du alle Parameter der Bot-Anweisungen, die für die Filterung relevant sind. Die mit einem Hashtag "#" markierten Kommentare sind lediglich für das Verständnis vonnöten und kein Teil des Programmcodes.

``` python
bot = Bot(max_likes_to_like=100,                 # Erklärung: maximale Anzahl der Likes bei 100
          max_followers_to_follow=2000,          # Erklärung: maximale Anzahl an Leuten, denen gefolgt werden soll (=200)
          min_followers_to_follow=10,		 # Erklärung: minimale Anzahl an Leuten, denen gefolgt werden soll (= 10)
          max_following_to_follow=10000,	 # Erklärung: maximale Gesamtanzahl an Followern (=10000)
          min_following_to_follow=10,            # Erklärung: minimale Anzahl an Followern (=10)
          max_followers_to_following_ratio=10,   # Erklärung: maximales Verhältnis von Followern zu gefolgten Personen (=10), d.h. die Zahl der Followern darf maximal 10x so groß sein wie die Anzahl der Leute, denen du folgst
          max_following_to_followers_ratio=2,    # Erklärung: maximales Verhältnis von gefolgten Personen zu Followern (=2), d.h. die Zahl der gefolgten Personen darf maximal doppelt so groß sein wie die Anzahl der Followern
          min_media_count_to_follow=3,		 # Erklärung: Mindestanzahl an medialen Inhalten, denen gefolgt wird (=3)
          stop_words=['shop', 'store', 'free'])
```
Wenn du die Werte für dich selber anpassen willst, modifiziere einfach die Zahlenangaben in der Funktion `bot = Bot ()` nach deinen Wünschen.

## User-Filterung

_Notation_: True - bedeutet, dass du abonnieren kannst, False - bedeutet, dass du es nicht kannst für folgende Konditionen:
* Wenn die Whitelist-Filterung "True" ist
* Wenn die Blacklist-Filterung "False" ist
* Wenn du bereits abonniert hast - "False"
* Wenn Business-Account "False" ist
* Wenn der bestätigte Account "False" ist
* Wenn die Anzahl an Followern kleiner ist als min_followers_to_follow - False
* Wenn die Anzahl an Followern größer ist als max_followers_to_follow - False
* Wenn die Anzahl an Follows kleiner ist als min_following_to_follow - False
* Wenn die Anzahl an Follows größer ist als max_following_to_followers_ratio - False
* Wenn das Verhältnis zwischen Follows / Followern größer ist als max_followers_to_following_ratio - False
* Wenn die Anzahl an Medieninhalten kleiner ist als min_media_count_to_follow - False,
* Wenn mindestens ein Stopp-Wort der stop_words Liste vorkommt im Namen oder in der Beschreibung (- False)
* Wenn es immer noch nicht gefiltert ist - True
