# Windows 11: Installation von Git Bash mit ZSH, oh-my-zsh und powerlevel10k

![Winfetch Windows Terminal](https://raw.githubusercontent.com/glenkusuma/github-gist/main/gitbash-with-zsh-omzsh-p10k/winfetch.png)

## 0. Video zu dieser Anleitung
:movie_camera: [Video - Windows 11: Git Bash und oh-my-zsh installieren](https://youtu.be/aqukKyAES7o)


## 1. Git Bash herunterladen & installieren

<https://git-scm.com/download/win>

## 2. ZSH herunterladen & installieren

### 1. Nerd Font herunterladen & installieren (für die spätere Verwendung in Git Bash und oh-my-zsh)
Du kannst deine eigenen Schriftarten auswählen und installieren.
Weitere Nerd Fonts findest du unter <https://www.nerdfonts.com/font-downloads>. 

In dieser Anleitung verwende ich `EnvyCodeR Nerd Font Mono` <https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.0/EnvyCodeR.zip>.
Entpacke die Dateien und doppelklicke zum Installieren.

### 2. Lade das neueste zsh-Paket herunter

<https://packages.msys2.org/package/zsh?repo=msys&variant=x86_64>

Beispiel:

```txt
zsh-5.9-2-x86_64.pkg.tar.zst
```

Das Paket ist mit `zst` komprimiert, daher benötigen wir einen "speziellen" Entpacker.  
In meinem Fall habe ich diese Datei heruntergeladen: <https://mirror.msys2.org/msys/x86_64/zsh-5.9-2-x86_64.pkg.tar.zst>
Und sie mit Peazip entpackt: <https://peazip.github.io/zst-compressed-file-format.html>.

### 3. Entpacke den Inhalt in dein Git Bash Installationsverzeichnis

Standardmäßig unter ```"C:\Program Files\Git"```

### 4. Teste und konfiguriere zsh

Öffne Git Bash und gib ein:

```bash
zsh
```

Dies ist ein wichtiger Schritt, `zsh` wird einige Konfigurationen abfragen, wie Tab-Vervollständigung, Verlauf usw. Bitte lies die Optionen und passe die Konfiguration an deine Bedürfnisse an.

### 5. Bearbeite die `~/.minttyrc` Datei (erstelle sie, falls sie nicht existiert)

```.minttyrc
BoldAsFont=no
Font=EnvyCodeR Nerd Font Mono
FontHeight=14
Columns=180
Rows=46
ScrollbackLines=2000
BackgroundColour=13,13,13
MiddleClickAction=void
RightClickAction=paste
Language=
BellType=0
BellFlash=yes
Printer=Microsoft Print to PDF
Transparency=off
CursorBlinks=yes
ThemeFile=nord
ForegroundColour=178,178,178
CursorColour=225,225,225
FontSmoothing=full
Locale=de_DE
Charset=UTF-8
Term=xterm-256color
BoldAsColour=no
CursorType=block
CtrlExchangeShift=yes
```

### 6. Konfiguriere git-prompt.sh

Wenn du diese Meldung erhältst:

`ERROR: this script is obsolete, please see git-completion.zsh`

Liegt das daran, dass etc\profile.d\git-prompt.sh die Shell nicht überprüft, bevor git-completion.bash eingebunden wird. Um dies zu beheben, kannst du eine leere Datei erstellen:

```bash
mkdir ~/.config/git

echo "" > ~/.config/git/git-prompt.sh
```

## 3. ZSH konfigurieren

### a. zsh als eigenständige Shell

Bearbeite `/etc/zsh/zshenv` und füge diese Zeile am Anfang der Datei hinzu:

```bash
PATH=/mingw64/bin/usr/bin:/usr/bin:/bin:$PATH
```

### b. ZSH als Standard-Shell beim Start von Git Bash konfigurieren

#### Bearbeite die Datei `C:\Program FIles\Git\etc\bash.bashrc`

Füge folgende Zeilen am Ende der Datei hinzu:

```bash
# Get user bash configuration ~/.bashrc
source ~/.bashrc;
```

#### Bearbeite die `~/.bashrc` Datei (erstelle sie, falls sie nicht existiert)

Füge folgende Zeilen am Ende der Datei hinzu:

```bash
# Launch Zsh
if [ -t 1 ]; then
exec zsh
fi
```

#### Schließe und öffne Git Bash erneut

## 4. Zsh Plugins installieren

### Installation der Plugins zsh-autosuggestions & zsh-syntax-highlighting

1. Installation & Ausführung

    ```bash
    git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH/plugins/zsh-autosuggestions
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH/plugins/zsh-syntax-highlighting

    source $ZSH/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
    source $ZSH/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
    ```

2. Bearbeite die `~/.zshrc` Datei

    ```zshrc
    plugins=( 
      ...
      zsh-autosuggestions
      zsh-syntax-highlighting
    )
    ```

## 5. Oh-my-zsh installieren
### Stelle sicher, dass der zip-Befehl im Path ist
Die Oh-My-Zsh Installation erwartet einen zip-Befehl wie unter Linux. 

1. GNUzip herunterladen
Um dies unter Windows zu emulieren, installiere das GNUzip32 Complete Paket <https://gnuwin32.sourceforge.net/packages/zip.htm>.

2. Bin-Verzeichnis zur Path-Umgebungsvariable hinzufügen
Füge anschließend das _bin_ Verzeichnis zu deinen Path-Umgebungsvariablen in Windows hinzu.

### Führe den folgenden Befehl in Git Bash aus

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 6. Powerlevel10k installieren

### 1. Powerlevel10k Installation

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

### 2. Standard-Theme festlegen
1. Bearbeite die `~/.zshrc` Datei
2. Suche nach "ZSH_THEME"
3. Ändere es zu ZSH_THEME="powerlevel10k/powerlevel10k"

### 3. Git Bash neu starten - p10k Konfigurations-Assistent startet
Dieser Schritt ist wichtig, `p10k` wird einige Konfigurationen für das Theme abfragen.  
Bitte lies die Optionen und stelle sie entsprechend deinen Bedürfnissen ein.
