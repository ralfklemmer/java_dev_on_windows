Die Einrichtung von Java auf Windows kann recht knifflig sein :unamused:. Besonders wenn der Bentzer keine Admin-Recht besitzt.
Daher habe ich ein Video und eine Anleitung geschrieben was genau zu tun ist.

**Diese Lösung basiert nicht auf WSL, da hierzu zwingend Admin-Rechte erforderlich sind.**

# Anleitung und Video
:mag: [01 - Windows 11: Git Bash und oh-my-zsh installieren](Step_1_Git_and_Console.md)

:movie_camera: [Video - Windows 11: Git Bash und oh-my-zsh installieren](https://youtu.be/aqukKyAES7o)

:mag: [02 - Windows 11: Java und Maven installieren](Step_2_Java_und_Maven.md)

:movie_camera: [Video - Windows 11: Java und Maven installieren](https://youtu.be/g1GmP9uFuMw)

:checkered_flag: Test des gesamten Setups mit Eclipse und IntelliJ:
:movie_camera: [Video - Windows 11: Windows 11: Eclipse und IntelliJ installieren](https://youtu.be/p-0A3OI62Ik)

# Wichtig
Wir installieren alles unter eurem Windows Benutzerordner. Dort legen wir folgende Ordnerstruktur an (z.B. für den Benutzer "ralf"):
```
/Users/ralf/dev/tools
/Users/ralf/dev/repo
```
# FAQ
Warum brauchen wir bei diesem Setup keine Admin-Rechte?

> Weil wir alles relevant unter deinem Benutzerverzeichnis installieren und hier hast du volle Kontrolle.

Warum verwenden wir kein WSL2?

> WSL2 ist super, aber die Lernkurve ist höher, denn ihr müsst erst damit zurecht kommen, dass ihr quasi zwei separate Computer verwalten müsst. Z.B. nur weil ihr unter WSL etwas installiert ist dies eurem Windows nicht bekannt.

Wann muss ich auf WSL umsteigen?

> Wenn du z.B. mit Docker arbeiten möchtest oder deine Software auf einem Linuxsystem testen oder bauen möchtest.

# Spezielle Tools für Windows 11
- Leichtgewichtiger Editor: z.B.: Sublime oder VSCode. Einfach kurz eine kleine Datei anzupassen ohne das lange Warten zum Laden einer großem IDE wie Eclipse oder IntelliJ.

# Optionale Tools
- [winget](https://winget.run/): Offizieller Paketmanager von Microsoft über den ihre schnell Programme installieren/updaten/deinstallieren könnt.
- [sdkman](https://sdkman.io/install/): Für die Verwaltung mehrere Java und Maven Versionen (ACHTUNG: Benötigt Adminrechte damit dies in der Git Bash richtig funktionert).
