# configuration.nix für memory

## Installation von Nixos

Damit du diese Konfiguration installieren kannst, brauchst du ein USB-Stick mit Nixos drauf.
Dafür kannst du das Image von der offiziellen [Nixos](https://nixos.org/download#download-nixos)
seite herunterladen und mit einem entsprechenden\* Tool auf den USB-Stick brennen.

Diesen USB-Stick kannst du nun in dein Zielgerät stecken. Starte nun dieses in das Boot-Menu 
(Bei Dell laptops auf F12 drücken beim starten). Setze das gerät auf UEFI-Mode und deaktiviere
Secure-Boot. Wähle nun den USB-Stick als Boot-Medium aus. Beim weissen Screen kannst du einfach
die erste Option auswählen (mit Enter). 

Nach dem das Geräte den Boot-Vorgang beendet hatt, solltest du ein Desktop sehen der ein wenig
dem von Windows ähnelt. Damit du Nixos installieren kannst brauchst du aber Internetzugang.
Um diesen einzurichten, kannst du auf das W-Lan-Symbol unten rechts auf dem Bildschirm klicken
und ein Netzwerk deiner Wahl einrichten.

Öffne nun den Installer erneut indem du auf die Windows-Taste drückst und installer eingibst.
Belasse die Sprache auf "American English" (damit du fehlermeldungen besser googeln kannst)
und gehe nun den Installer Schritt für Schritt durch. Und wähle folgende Einstellungen aus:

 - Keyboard Layout: German (Swiss)
 - Username: user (Der user mus so heissen sonst wirst du später probleme haben)
 - Password: password
 - Require strong password: no 
 - Login automaticaly without asking for the password: yes
 - Use the same password for the administrator account: yes
 - Desktop: Plasma
 - Allow unfree software: yes
 - Partitions: Erase disk & Swap (no Hybernate)
 - Encrypt System: no

 Drücke nun auf "Next" und damm auf "Install". Nun wird Nixos installiert.
Sobald Nixos installiert ist, kannst du das System neustarten und den USB-Stick entfernen.

Öffne, sobald du im neuen System bist, eine Konsole (Shortcut: Ctrl + Alt + t) und gebe 
folgende Comands nacheinander ein.

``` sh
nix-shell -p git

git clone https://github.com/chlyNiklas/memory-nix.git
sudo cp /etc/nixos/hardware-configuration.nix ./
sudo rm /etc/nixos/*
sudo cp memory-nix/* /etc/nixos/
sudo mv hardware-configuration /etc/nixos

sudo nixos-rebuild switch --flake /etc/nixos#default

reboot 0
```



\* z.B. [Rufus](https://rufus.ie/en/) *(nur für Windows verfügbar)* oder [Etcher](https://etcher.balena.io/)

## Konfiguration anwenden:

``` sh
sudo nixos-rebuild switch --flake /etc/nixos#default
```

## Memory anleitungen herunterladen

``` sh
init-memory
```
