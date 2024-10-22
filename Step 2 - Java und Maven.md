# Java und Maven Installation

## Java
1. Ein Java JDK (Java Development Kit) herunterladen. Z.B.: von [jdk.java.net](https://jdk.java.net/).
2. Zip entpacken und an einen gewünscheten Ort kopieren z.B. C:\Users\myname\dev\tools\java\java23.
3. Benutzer-Umgebungsvariable anpassen
JAVA_HOME hinzufügen: Eintrag lautet JAVA_HOME="C:\Users\myname\dev\tools\java\java23"
Path anpassen: Eintrag %JAVA_HOME%\bin hinzufügen
4. Testen, ob Java korrekt installiert wurde
Eine neue Eingabeaufforderung oder Git Bash aufmachen und folgenden Befehle ausführen:

```
java -version
```

Die gerade konfigurierte Java Version sollte angezeigt werden.

## Maven
1. [Maven heruntenladen](https://maven.apache.org/download.cgi)
2. Zip entpacken und an einen gewünscheten Ort kopieren z.B. C:\Users\myname\dev\tools\maven
3. Benutzer-Umgebungsvariable anpassen
M2_HOME hinzufügen: Eintrag lautet M2_HOME="C:\Users\myname\dev\tools\maven"
Path anpassen: Eintrag %M2_HOME%\bin hinzufügen
4. Testen, ob Maven korrekt installiert wurde
Eine neue Eingabeaufforderung oder Git Bash aufmachen und folgenden Befehle ausführen:

```
mvn -v
```

Jetzt sollte die Maven Version und die verwendete Java Version angezeigt werden.

## Java Version wechseln
Für einen Wechsel muss die JAVA_HOME auf eine andere Java-Installation umgestellt werden.
