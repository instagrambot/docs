# Installationsanleitung f�r Windows

**Wichtig! Lies die dir Anleitungen von Anfang bis zum Ende sorgf�ltig durch um das Bot zu starten. Viel Gl�ck!**

## Installiere Python 3

1. �ffne die Seite [website](https://www.python.org/downloads/).
2. W�hle die Version, die zu dir passt (abh�ngig vom Betriebssystem).
3. Download.
4. F�hre den Installer durch.
5. Folge den Anweisungen des Installers. Klicke "Add Python 3.x to Path" und w�hle "Installiere jetzt". Wenn du ein fortgeschrittener Anwender bist, w�hle "Customized Installation".

![Install Python 3 and add to PATH](../img/install_python_on_Windows.PNG "Install Python 3 and add to PATH").

## Download ein Projekt von GitHub

Es gibt zwei Optionen, um ein Projekt herunterzuladen:

a) Klicke auf den Link https://github.com/instagrambot/instabot. Klick auf "Clone or download" und hiernach auf "Download ZIP". Entpacke die ZIP-Datei.
b) Installiere den Git-Clienten:
1. Gehe zu Git [site](https://git-scm.com/downloads).
2. W�hle die Version, die zu dir passt (abh�ngig vom Betriebssystem).
3. Download.
4. F�hre den Installer durch.
5. Folge den Anweisungen des Installers (klicke auf "Weiter"). Wenn du ein fortgeschrittener Anwender bist, kannst du den Clienten manuell installieren.
6. Nach erfolgreicher Installation �ffne die Eingabeaufforderung.
7. In der Eingabeaufforderung gib folgendes ein:

``` bash
git clone https://github.com/instagrambot/instabot --recursive
```
Und dr�cke Enter.

***Herzlichen Gl�ckwunsch! Du hast das Projekt erfolgreich heruntergeladen!***

## Installiere Instabot in einer virtuellen Python-Umgebung.

In der Eingabeaufforderung, gib ein:

``` python
pip install -U instabot
```
Und dr�cke "Enter".
