# System setups
How to setup my personal computers.

## Windows 11 (Home & Pro)

### **Installation**

#### **Skip Microsoft Login**

Microsoft wants a Microsoft account while installing Windows. To skip this step,
press `Shift` + `F10` to open the command prompt and type:

```cmd
OOBE\BYPASSNRO
```

This will allow you to create a local account.

### **Settings**

#### **Network & Internet**

- `Network & Internet` > `Properties`: Mark as `Private Network`

#### **Languages**

- `Time & language` > `Language & region` > `Windows display language`:
  - `English (United States)`

- `Time & language` > `Language & region` > `Preferred languages`:
  - `English (United States)`
  - `English (United Kingdom)`
  - `English (Germany)`
  - `German (Germany)`

- `Time & language` > `Language & region` > `Country or region`:
  - `Germany`

- `Time & language` > `Language & region` > `Regional formats` > `Calendar`:
  - `Gregorian Calendar`

- `Time & language` > `Language & region` > `Regional formats` > `First day of week`:
  - `Monday`

- `Time & language` > `Language & region` > `Regional formats` > `Short date`:
  - `2017-04-05`

- `Time & language` > `Language & region` > `Regional formats` > `Long date`:
  - `Wednesday, April 5, 2017`

- `Time & language` > `Language & region` > `Regional formats` > `Short time`:
  - `09:40`

- `Time & language` > `Language & region` > `Regional formats` > `Long time`:
  - `09:40:07`

- `Time & language` > `Language & region` > `Regional formats` > `Standard digits`:
  - `0123456789`

#### **Date & Time**

- `Time & language` > `Date & time` > `Time zone`:
  - `(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna`

- `Personalization` > `Taskbar` > `Taskbar behaviors`:
  - [x] `Show seconds in system tray clock`

#### **Typing** 

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Override for default input method`:
  - `Use language list (recommended)`

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Switching input methods`:
  - [ ] `Let me use a differernt input method for each app window`
  - [x] `Use the desktop langugae bar when it's available`

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Language bar options`:
  - `Language Bar` > `Hidden` \
  - [ ] `Show the Language bar as transparent when inactive`
  - [ ] `Show additional Language bar icons in the taskbar`
  - [ ] `Show text labels on the Language bar`

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Input language hot keys`:
  - `To turn of Caps Lock` > `Press the CAPS LOCK key`
  - `Hot keys for input language:`
  - `Between input languages` > `(None)`
  - `To English (United Kingdom) - German` > `(None)`
  - `To English (United States) - German` > `(None)`
  - `To German (Germany) - German` > `(None)`

#### **Registry**

Disable Web Results in Windows Search:

```cmd
HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows
```
`New` > `Key` with name `Explorer`

```cmd
HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Explorer
```
`New` > `DWORD (32-bit) Value` with name `DisableSearchBoxSuggestions`.

Set the value of the new `DWORD` to `1`.

Reboot the system after all changes are done.

#### **Hyper-V**
[Virtualization applications don't work together with Hyper-V, Device Guard, and Credential Guard](https://learn.microsoft.com/en-us/troubleshoot/windows-client/application-management/virtualization-apps-not-work-with-hyper-v)

Make sure Hyper-V is disabled, since it cannot work together with other
virtualization applications. Run the following commands in an elevated
powershell terminal.

```powershell
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V
```

If it's enabled, disable it:

```powershell
Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Hypervisor
```

Reboot the system.

#### **Windows Subsystem for Linux**
[Install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

To install Linux (Ubuntu by default), run the following command in an elevated
powershell terminal.

```powershell
wsl --install
```

Reboot the system.

Create the default linux user.

Update system:

```bash
sudo apt update && sudo apt upgrade -y
```

Follow the steps in [Windows Subsystem for Linux](#windows-subsystem-for-linux-1)

#### **Powershell**

1. Install `oh-my-posh`:
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; Invoke-Expression ((New-Object System.Net.WebClient).DownloadString('https://ohmyposh.dev/install.ps1'))
    ```

2. Install the latest version of `PowerShellGet`:
    ```powershell
    Install-Module -Name PowerShellGet -Force
    ```

3. Install `PSReadLine`:
    ```powershell
    Install-Module PSReadLine
    ```

4. Create Powershell profile:
    ```powershell
    notepad $PROFILE
    ```
    ```powershell
    Import-Module PSReadLine
    Set-PSReadLineOption -PredictionSource History

    oh-my-posh init pwsh | Invoke-Expression
    oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/quick-term.omp.json" | Invoke-Expression
    ```

#### **Fonts**

#### **Windows Terminal**

Set the terminal font to `JetBrainsMono NF`.

### **Applications**

#### **Microsoft Edge**
TBD

#### **Mozilla Firefox**
[Download Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/)

Login with the account to sync history and extensions. Make sure all extensions
can be run in private windows.

Additional changes in settings:

`Search` > `Search Shortcuts` remove all Search Engines.

`about:config`:
- `browser.link.open_newwindow.restriction`: `0`

#### **Google Chrome**
[Download Google Chrome](https://www.google.com/chrome/)

TBD

#### **Bitwarden**
[Download Bitwarden](https://bitwarden.com/download/)

#### **Printer Drivers**
[Download Epson Drivers](https://epson.com/Support/Printers/All-In-Ones/WorkForce-Series/Epson-WorkForce-Pro-WF-3720/s/SPT_C11CF24201?review-filter=Windows+11)

[Download NAPS2](https://www.naps2.com/)

#### **Visual Studio Code**
[Download Visual Studio Code](https://code.visualstudio.com/)

Login to sync all settings and extensions.

Create a `custom.css` in `~/.vscode` with the following content:
```css
.explorer-viewlet {
  font-family: "JetBrainsMono NF" !important;
}
```

Restart VSCode with administrative permissions and enable `Custom CSS and JS Loader`.

#### **Oracle VirtualBox**
[Download VirtualBox](https://www.virtualbox.org/)

#### **HashiCorp Vagrant**
[Download Vagrant](https://www.vagrantup.com/)

#### **Docker Desktop**
[Download Docker Desktop](https://www.docker.com/products/docker-desktop/)

To use Docker on Windows without Docker Desktop it, needs to be installed in
WSL.

Disable Docker integration in WSL2:

`Settings` > `Resources` > `WSL Integration`: Disable all

To make sure containers don't have DNS problems, add this to the Docker
configuration:

```json
{
  "dns": ["1.1.1.1", "1.0.0.1", "8.8.8.8", "8.8.4.4"]
}
```

### **Windows Subsystem for Linux**

#### **Network & DNS**
[Custom DNS settings for WSL](https://superuser.com/questions/1533291/how-do-i-change-the-dns-settings-for-wsl2)

1. To disable the generation of `/etc/resolv.conf`, paste into `/etc/wsl.conf`:
    ```ini
    [network]
    generateResolvConf = false
    ```

2. Restart WSL:
    ```powershell
    wsl --shutdown
    ```

3. Open a new WSL terminal.

4. Write into `/etc/resolv.conf`:
    ```ini
    nameserver 1.1.1.1
    nameserver 1.0.0.1
    nameserver 8.8.8.8
    nameserver 8.8.4.4
    ```

2. Restart WSL:
    ```powershell
    wsl --shutdown
    ```

#### **Custom Shell**

1. Install `oh-my-posh`:
    ```bash
    sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
    ```
    ```bash
    sudo chmod +x /usr/local/bin/oh-my-posh
    ```

2. Install `zsh`:
    ```bash
    sudo apt install zsh
    ```

3. Install `oh-my-zsh`:
    ```bash
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended
    ```

4. Install `oh-my-zsh` plugins:
    ```bash
    git clone https://github.com/zsh-users/zsh-autosuggestions "${HOME}/.oh-my-zsh/custom/plugins/zsh-autosuggestions" --depth 1 \
    && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git "${HOME}/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting" --depth 1 \
    && git clone https://github.com/zsh-users/zsh-history-substring-search "${HOME}/.oh-my-zsh/custom/plugins/zsh-history-substring-search" --depth 1 \
    && git clone https://github.com/hlissner/zsh-autopair "${HOME}/.oh-my-zsh/custom/plugins/zsh-autopair" --depth 1
    ```

5. Add `.dircolors`:
    ```bash
    dircolors --print-database > ~/.dircolors
    ```

6. Change the value of `OTHER_WRITEABLE` to `01;96`

7. Add to `.zshrc`:
    ```bash
    export ZSH="$HOME/.oh-my-zsh"
    export HIST_STAMPS="%Y-%m-%d %T"
    export POSH_THEMES_PATH="/mnt/c/Users/handarel/AppData/Local/Programs/oh-my-posh/themes"

    zstyle ':omz:update' mode disabled

    plugins=(
      git
      git-auto-fetch
      command-not-found
      dotenv
      gpg-agent
      ssh-agent
      rsync
      zsh-autopair
      zsh-autosuggestions
      zsh-syntax-highlighting
      zsh-history-substring-search
    )

    source $ZSH/oh-my-zsh.sh

    eval "$(dircolors ~/.dircolors)"
    eval "$(oh-my-posh init zsh --config $POSH_THEMES_PATH/quick-term.omp.json)"

    function llc() {
      /usr/bin/ls -hlvA --time-style="+%Y-%m-%d %H:%M:%S" --group-directories-first --color=always $1 | awk '
        BEGIN {
          FPAT = "([[:space:]]*[^[:space:]]+)";
          OFS = "";
        }
        {
          $1 = "\033[38;2;222;222;222m" $1 "\033[0m"; # permissions
          $2 = "\033[38;2;97;214;214m"  $2 "\033[0m"; # directory size
          $3 = "\033[38;2;222;222;222m" $3 "\033[0m"; # user
          $4 = "\033[38;2;222;222;222m" $4 "\033[0m"; # group
          $5 = "\033[38;2;97;214;214m"  $5 "\033[0m"; # size
          $6 = "\033[38;2;222;222;222m" $6 "\033[0m"; # date
          $7 = "\033[38;2;120;120;120m" $7 "\033[0m"; # time
          # $8 = "\033[38;2;80;80;80m"    $8 "\033[0m"; # timezone
          print
        }
      '
    }
    alias ll="llc"
    ```
