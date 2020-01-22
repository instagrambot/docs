# Wie installiere ich das Bot in Unix? (Linux, macOS)
* Öffne das Terminal und führe folgenden Befehl durch:
```
pip install -U instabot
git clone https://github.com/instagrambot/instabot --recursive
cd instabot/examples
```

* Hiernach kannst du jedes fertige Skript in analoger Weise exekutieren:
```
python multi_script_CLI.py
```

## Fehler

* Wenn du den Fehler `pip: command not found` erhältst, versuche bitte folgendes:
```
sudo easy_install pip
```

* Wenn du die Nachricht `permission denied` erhältst, nachdem du `pip install -U instabot` eingegeben hast, versuche:
```
sudo pip install -U instabot
```

* Wenn du immer noch die Nachricht `permission denied` erhältst, nachdem du `sudo pip install -U instabot` eingegeben hast, versuche den folgenden Befehl:
```
sudo -H pip install -U instabot
```
