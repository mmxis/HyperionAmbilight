Hyperion Ambilight
==============

Anschluss des Raspberry Pi's

![image](https://user-images.githubusercontent.com/71505911/181065473-e10386df-3162-4d85-9415-eb94082a361a.png)



Korrekter Aufbau:
![image](https://user-images.githubusercontent.com/71505911/181065553-166ebf8e-2335-43e4-aa93-d7809bfe3db1.png)


Tutorial:
1. Gehe auf die OSMC Download Seite. https://osmc.tv/download/
2. Klicke ganz unten auf „Disk Images“ und lade das neuste Release für „Raspberry Pi 2 / 3“. Entpacke es danach mit WinRar, 7Zip o.ä.
3. Übertrage das heruntergeladene und entpackte Image (Dateityp: .img) auf deine micro SD Karte.
4. Nach Übertragung kannst du die Micro SD Karte in den Raspberry Pi stecken.
5. Schließe HDMI des Fernsehers, Tastatur und Maus an den Raspberry Pi an und starte ihn (durch verbinden des micro USB Stromanschlusses).
6. Nach kurzem Warten kannst du die Sprach-, Tastur- und Zeiteinstellungen festlegen.
7. Lasse den Hostnamen auf „osmc“ und aktiviere SSH („SSH Service is enabled“). Akzeptiere anschließend die Lizenzbedingungen.
8. Wähle das OSMC Theme (nicht Classic).
9. Den Newsletter musst du nicht auswählen.
10. Beende das Setup.
11. Optimal: Wähle unter Programme -> My OSMC -> Network -> Wireless -> Enable Adapter dein WLAN aus und gib das Passwort ein. Sonst ist eine Verbindung per LAN Kabel mit deinem Netzwerk nötig (zumindest temporär).
12. Finde unter Einstellungen -> Systeminfo -> Netzwerk -> IP-Adresse die lokale IP-Adresse des Raspberry Pi’s in deinem Netzwerk heraus (192.168.x.x).



Hyperion installieren
Ab jetzt werden die externen Peripheriegeräte nicht mehr gebraucht, da wir uns per SSH einloggen. In Windows geht dies am einfachsten per Putty (hier erklärt). Der Hostname ist „osmc“ (sofern du ihn nicht geändert hast) bzw. die IP Adresse, die du eben in Schritt 12 ausgelesen hast. Falls die Verbindung damit nicht funktioniert, obwohl sich der PC im selben Netzwerk befindet, musst du in deinem Router die interne IP Adresse (192.168.x.x) herausfinden.

Der Standard-Username ist osmc, ebenso wie das Passwort standardmäßig osmc ist.

Nach dem Login muss zunächst SPI aktiviert werden, wozu wir eine Datei bearbeiten müssen:

---------------
sudo nano /boot/config.txt
---------------

Am Ende der Datei fügen wir folgende Zeile hinzu:

---------------
dtparam=spi=on
---------------

Damit die Änderungen übernommen werden, muss der Raspberry Pi neu gestartet werden:

sudo reboot

Dabei wird die SSH Verbindung unterbrochen. Du musst dich erneut verbinden.

Wir überprüfen nun noch, ob der SPI Datenbus wirklich aktiviert wurde. Dafür geben wir ein:

ls /dev/spidev*

Es sollten nun die verfügbaren Pfade angezeigt werden. Falls nichts angezeigt wird, wurde SPI nicht aktiviert.
