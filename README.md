# System setups
How to setup my personal systems.

## Windows 11

### **Installation**

#### **Skip Microsoft Login**

Microsoft wants a Microsoft account while installing Windows. To skip this step,
press `Shift` + `F10` to open the command prompt and type:

```cmd
OOBE\BYPASSNRO
```

This will allow you to create a local account.

### **Settings**

#### **Languages**

- `Time & language` > `Language & region` > `Windows display language`:
  > `English (United States)`

- `Time & language` > `Language & region` > `Preferred languages`:
  > `English (United States)` \
  > `English (United Kingdom)` \
  > `English (Germany)` \
  > `German (Germany)`

- `Time & language` > `Language & region` > `Country or region`:
  > `Germany`

- `Time & language` > `Language & region` > `Regional formats` > `Calendar`:
  > `Gregorian Calendar`

- `Time & language` > `Language & region` > `Regional formats` > `First day of week`:
  > `Monday`

- `Time & language` > `Language & region` > `Regional formats` > `Short date`:
  > `2017-04-05`

- `Time & language` > `Language & region` > `Regional formats` > `Long date`:
  > `Wednesday, April 5, 2017`

- `Time & language` > `Language & region` > `Regional formats` > `Short time`:
  > `09:40`

- `Time & language` > `Language & region` > `Regional formats` > `Long time`:
  > `09:40:07`

- `Time & language` > `Language & region` > `Regional formats` > `Standard digits`:
  > `0123456789`

#### **Date & Time**

- `Time & language` > `Date & time` > `Time zone`:
  > `(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna`

#### **Typing** 

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Override for default input method`:
  > `Use language list (recommended)`

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Switching input methods`:
  > [ ] `Let me use a differernt input method for each app window` \
  > [x] `Use the desktop langugae bar when it's available`

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Language bar options`:
  > `Language Bar` > `Hidden` \
  > [ ] `Show the Language bar as transparent when inactive` \
  > [ ] `Show additional Language bar icons in the taskbar` \
  > [ ] `Show text labels on the Language bar`

- `Time & language` > `Typing` > `Advanced keyboard settings` > `Input language hot keys`:
  > `To turn of Caps Lock` > `Press the CAPS LOCK key` \
  > `Hot keys for input language:` \
  > `Between input languages` > `(None)` \
  > `To English (United Kingdom) - German` > `(None)` \
  > `To English (United States) - German` > `(None)` \
  > `To German (Germany) - German` > `(None)`

#### **Hyper-V**

Make sure Hyper-V is disabled, since it cannot work together with other
virtualization applications:

```powershell
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V
```

If it's enabled, disable it:

```powershell
Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Hypervisor
```

Reboot the system.

### **Applications**

#### **Microsoft Edge**


#### **Mozilla Firefox**
[Download Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/)

`about:config`:
- `browser.link.open_newwindow.restriction`: `0`

#### **Google Chrome**
[Download Google Chrome](https://www.google.com/chrome/)

#### **Bitwarden**
[Download Bitwarden](https://bitwarden.com/download/)

#### **Printer Drivers**
[Download Epson Drivers](https://epson.com/Support/Printers/All-In-Ones/WorkForce-Series/Epson-WorkForce-Pro-WF-3720/s/SPT_C11CF24201?review-filter=Windows+11)

[Download NAPS2](https://www.naps2.com/)
