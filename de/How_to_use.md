# Anleitungen zur Nutzung

**Wichtig! Lies die dir Anleitungen von Anfang bis zum Ende sorgfältig durch um das Bot zu starten. Viel Glück!**

## Wie funktioniert es?

Du benötigst eines der heruntergeladenen Projekte. Im ***instabot/examples/*** Ordner sind fertige Skripts, mit denen du arbeiten kannst.

## Wie führe ich das Skript durch?

Öffne die Eingabeaufforderung, nutze ***cd*** um zum korrekten Ordner-Pfad zu gelangen (dessen Name ***instabot/examples*** lautet). Gib ein:

``` python
python name.py param
```

Wobei ***name*** der Name des Skriptes ist und ***param*** der benötigte Parameter, um das Skript zu starten. Nicht jedes Skript benötigt zusätzliche Parameter.

## Woher weiß ich, ob ich Parameter eingeben muss für das Skript?

Führe das Skript durch mithilfe des folgenden Befehls:

``` python
python name.py
```

Falls weitere Parameter benötigt werden, wird das Skript stoppen und dir eine Nachricht anzeigen, welche Parameter benötigt werden.

Beispiel.
Führe das folgende Skript durch:

``` python
python like_hashtags.py. 
```
Das Skript stoppt und zeigt folgende Fehlernachricht:

``` python
error: the following arguments are required: hashtags.
```

Das heißt, wir benötigen Hashtags als Parameter. Um dies zu korrigieren:

``` python
python like_hashtags.py folgen
```

## All-inklusiv

***multi_script_CLI.py*** ist ein Skript mit allen Funktionen. Wenn du es das erste Mal startest, wirst du nach der Konfiguration gefragt. Die Einstellungen sind in der ***setting.txt*** Datei zu finden. Es werden zudem die folgenden Dateien erstellt: ***hashtag_file.txt, users_file.txt, whitelist.txt, blacklist.txt, comment.txt***

## 24/7

Ja, es gibt ein Skript, das rund um die Uhr Leuten folgt und entfolgt sowie Fotos durch Nickanmen und Hashtags liked. Dies wird alles durch das Skript ***ultimate.py*** erledigt.

## Zeitplanung

Es gibt ebenfalls ein Skript, das nach deiner persönlichen Zeitplanung läuft. Das Skript heißt ***ultimate.py*** im ***instabot/examples/ultimate_schedule*** Ordner. Du kannst es öffnen und den Code mit jedem Editor (z.B. Texteditor) bearbeiten und anpassen. Da es bereits Kommentare im wichtigen Teil des Codes gibt, sollte dir das leicht fallen!

## Wie konfiguriere ich das Skript korrekt

Um sicherzugehen, dass dein Account nicht gesperrt wurde, musst du das Skript konfigurieren. Sagen wir du möchtest Fotos bestimmter Hashtags jede Minute liken. Zunächst benötigen wir die Zeit in Sekunden. Öffne ***like_hashtags.py*** mit einem Texteditor. Finde die richtige Zeile des Programmcodes. Es sollte folgendermaßen aussehen:

``` python
bot = Bot()
bot.login(username=args.u, password=args.p,
          proxy=args.proxy)
```

Als nächstes finden wir:

``` python
bot = Bot()
```

Wir müssen einen Parameter in die Klammern einfügen. Dieser Parameter lautet ***like_delay***. Wir setzen den Wert auf 60, weil wir im Minutenabstand Fotos bestimmter Hashtags liken möchten. Am Ende würde es folgendermaßen aussehen.

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























