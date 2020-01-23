# Anleitungen zur Nutzung

**Wichtig! Lies die dir Anleitungen von Anfang bis zum Ende sorgf�ltig durch um das Bot zu starten. Viel Gl�ck!**

## Wie funktioniert es?

Du ben�tigst eines der heruntergeladenen Projekte. Im ***instabot/examples/*** Ordner sind fertige Skripts, mit denen du arbeiten kannst.

## Wie f�hre ich das Skript durch?

�ffne die Eingabeaufforderung, nutze ***cd*** um zum korrekten Ordner-Pfad zu gelangen (dessen Name ***instabot/examples*** lautet). Gib ein:

``` python
python name.py param
```

Wobei ***name*** der Name des Skriptes ist und ***param*** der ben�tigte Parameter, um das Skript zu starten. Nicht jedes Skript ben�tigt zus�tzliche Parameter.

## Woher wei� ich, ob ich Parameter eingeben muss f�r das Skript?

F�hre das Skript durch mithilfe des folgenden Befehls:

``` python
python name.py
```

Falls weitere Parameter ben�tigt werden, wird das Skript stoppen und dir eine Nachricht anzeigen, welche Parameter ben�tigt werden.

Beispiel.
F�hre das folgende Skript durch:

``` python
python like_hashtags.py. 
```
Das Skript stoppt und zeigt folgende Fehlernachricht:

``` python
error: the following arguments are required: hashtags.
```

Das hei�t, wir ben�tigen Hashtags als Parameter. Um dies zu korrigieren:

``` python
python like_hashtags.py folgen
```

## All-inklusiv

***multi_script_CLI.py*** ist ein Skript mit allen Funktionen. Wenn du es das erste Mal startest, wirst du nach der Konfiguration gefragt. Die Einstellungen sind in der ***setting.txt*** Datei zu finden. Es werden zudem die folgenden Dateien erstellt: ***hashtag_file.txt, users_file.txt, whitelist.txt, blacklist.txt, comment.txt***

## 24/7

Ja, es gibt ein Skript, das rund um die Uhr Leuten folgt und entfolgt sowie Fotos durch Nickanmen und Hashtags liked. Dies wird alles durch das Skript ***ultimate.py*** erledigt.

## Zeitplanung

Es gibt ebenfalls ein Skript, das nach deiner pers�nlichen Zeitplanung l�uft. Das Skript hei�t ***ultimate.py*** im ***instabot/examples/ultimate_schedule*** Ordner. Du kannst es �ffnen und den Code mit jedem Editor (z.B. Texteditor) bearbeiten und anpassen. Da es bereits Kommentare im wichtigen Teil des Codes gibt, sollte dir das leicht fallen!

## Wie konfiguriere ich das Skript korrekt

Um sicherzugehen, dass dein Account nicht gesperrt wurde, musst du das Skript konfigurieren. Sagen wir du m�chtest Fotos bestimmter Hashtags jede Minute liken. Zun�chst ben�tigen wir die Zeit in Sekunden. �ffne ***like_hashtags.py*** mit einem Texteditor. Finde die richtige Zeile des Programmcodes. Es sollte folgenderma�en aussehen:

``` python
bot = Bot()
bot.login(username=args.u, password=args.p,
          proxy=args.proxy)
```

Als n�chstes finden wir:

``` python
bot = Bot()
```

Wir m�ssen einen Parameter in die Klammern einf�gen. Dieser Parameter lautet ***like_delay***. Wir setzen den Wert auf 60, weil wir im Minutenabstand Fotos bestimmter Hashtags liken m�chten. Am Ende w�rde es folgenderma�en aussehen.

``` python
bot = Bot(like_delay=60)
bot.login(username=args.u, password=args.p,
          proxy=args.proxy)
```

## Parameter-Liste

| Parameter| Beschreibung | Beispiel |
| ------------- |:-------------:| ------:|
| proxy | Proxy for Instabot | None|
| max_likes_per_day| How many likes the bot will perform per day| 1000|
| max_unlikes_per_day | How many medias the bot will unlike in a day| 1000|
| max_follows_per_day| Max number of follow per day| 350|
| max_unfollows_per_day| Max number of unfollow per day| 350|
| max_comments_per_day| Max number of comments per day| 100|
| max_likes_to_like| If the media has more likes then this value - it will be ignored and not be liked | 200|
| filter_users | Filter users if True | True|
| max_followers_to_follow| If the user has more followers than this value - the user will not be followed or liked. | 2000|
| min_followers_to_follow| If the user has fewer followers than this value - the user will not be followed or liked.| 10|
| max_following_to_follow| If the user has more followings than this value - the user will not be followed or liked.| 10000|
| min_following_to_follow| If the user has fewer followings than this value - the user will not be followed or liked.| 10|
| max_followers_to_following_ratio| if the user's followers/following is greater than this value - the user will not be followed or liked.| 10|
| max_following_to_followers_ratio| if user's following/followers is greater than this value - he will not be followed or liked.| 2|
| min_media_count_to_follow| If the user has fewer media count than this value - the user will not be followed. | 3|
|max_following_to_block|If the user have a following more than this value - the user will be blocked in blocking scripts because he is a massfollower| 2000|
| max_likes_to_like | Max number of likes that can media have to be liked | 100 |
| like_delay | Delay between likes in seconds| 10|
| unlike_delay | Delay between unlikes in seconds | 10|
| follow_delay | Delay between follows in seconds| 30|
| unfollow_delay | Delay between unfollows in seconds| 30|
| comment_delay | Delay between comments in seconds|  60|
| whitelist | Path to the file with users that shouldn't be unfollowed| "whitelist.txt"|
| blacklist | Path to the file with users that shouldn't be followed, liked or commented | "blacklist.txt"|
| comments_file | Path to the comments database | "comments.txt" |
| stop_words| A list of stop words: don't follow a user if they have any of these stop words in their description| ['shop', 'store', 'free']|























