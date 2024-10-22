# Install Git Bash with ZSH, OH MY ZSH & POWERLEVEL10K | Windows Guide

![Winfetch Windows Terminal](https://raw.githubusercontent.com/glenkusuma/github-gist/main/gitbash-with-zsh-omzsh-p10k/winfetch.png)

## 1. Download & Install Git Bash

<https://git-scm.com/download/win>

## 2. Download & Install ZSH

### 1. Download & Install Nerd Font (for later usage in Git Bash and oh-my-zsh)
You can choose & install your own fonts.
Other Nerd fonts can be found on <https://www.nerdfonts.com/font-downloads>. 

In this guide I'm using `EnvyCodeR Nerd Font Mono` <https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.0/EnvyCodeR.zip>.
Unzip the files and double-click to install.

### 2. Download the latest zsh package

<https://packages.msys2.org/package/zsh?repo=msys&variant=x86_64>

Example:

```txt
zsh-5.9-2-x86_64.pkg.tar.zst
```

The package is compacted using `zst`, so we need some "special" extractor.  
In my case, I've downloaded this file   <https://mirror.msys2.org/msys/x86_64/zsh-5.9-2-x86_64.pkg.tar.zst>
And extracted it using the Peazip.  <https://peazip.github.io/zst-compressed-file-format.html>.

### 3. Extract the content to your git bash installation dir

By default in ```"C:\Program Files\Git"```

### 4. Test it and configure zsh

Open git bash and type:

```bash
zsh
```

This is a important step, `zsh` will ask a few configurations, like the tab completion, history, etc.  Please read the options and set the config to your use.

### 5. Edit the `~/.minttyrc` file. (create it if it doesn't exist)

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

### 6. Configure git-prompt.sh

If you get this message:

`ERROR: this script is obsolete, please see git-completion.zsh`

It is because etc\profile.d\git-prompt.sh does not check the shell before including git-completion.bash. To fix it you can create an empty file:

```bash
mkdir ~/.config/git

echo "" > ~/.config/git/git-prompt.sh
```

## 3. Configuring zsh

### a. zsh as standalone shell

edit `/etc/zsh/zshenv` and add this line at the begining of the file:

```bash
PATH=/mingw64/bin/usr/bin:/usr/bin:/bin:$PATH
```

### b. Configuring zsh as default shell when launching Git Bash

#### Edit the `C:\Program FIles\Git\etc\bash.bashrc> file

Add the following lines at the end of the file

```bash
# Get user bash configuration ~/.bashrc
source ~/.bashrc;
```

#### Edit the `~/.bashrc` file. (create it if it doesn't exist)

Add the following lines at the end of the file

```bash
# Launch Zsh
if [ -t 1 ]; then
exec zsh
fi
```

#### Close and open again the git bash

## 4. Install Zsh plugins

### install zsh-autosuggestions & zsh-syntax-highlighting plugin

1. Install & Run

    ```bash
    git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH/plugins/zsh-autosuggestions
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH/plugins/zsh-syntax-highlighting

    source $ZSH/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
    source $ZSH/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
    ```

2. edit `~/.zshrc` file

    ```zshrc
    plugins=( 
      ...
      zsh-autosuggestions
      zsh-syntax-highlighting
    )
    ```

## 5. Install oh-my-zsh
### Ensure zip command is in Path
Oh-My-Zsh installation expects a zip command link on Linux is available. 

1. Download GNUzip
To emulate this on Windows install the GNUzip32 Complete package <https://gnuwin32.sourceforge.net/packages/zip.htm>.

2. Add bin-directory to Path environment variable
After that add the _bin_ directory to your path environment variables in Windows.

### execute the following cmd on git bash  

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 6. Install Powerlevel10k

### 1. Install Powerlevel10k

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

### 2. Set default theme
1. edit `~/.zshrc` file
2. search for "ZSH_THEME"
3. Change to ZSH_THEME="powerlevel10k/powerlevel10k"

### 3. Restart Git Bash - p10k Configuration Wizard starts
So, this step is important, the `p10k` will ask a few configurations for the theme.  
Please read the options and set that according to your use.
