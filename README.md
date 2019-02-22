# Windows

## Install chocolatey:

1. Open `cmd.exe` as Administrator:
2. Run:
```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

## Install choco dependencies
Open PowerShell as Administrator and run:

```
.\windows\install-choco-dependencies.bat
```

## Install WSL
Open PowerShell as Administrator and run:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

Now open Microsoft Store and install Ubuntu 18.04

## Configure Hyper
Copy `.hyper.js` to `c:\Users\carlo\.hyper.js` and overwrite.

## Git and GitHub
We need to configure git twice, once for Windows apps like VS Code
and another time for the WSL:
1. Open `Git GUI` and generate an SSH key
2. Add to permitted GitHub SSH keys in GitHub settings
3. Open `Git Bash` windows app
4. Configure git:
```
git config --global user.email "email@example.com"
git config --global user.name "Carlos Baraza"
```
5. Finally add github.com to `known_hosts`:
```
ssh-keyscan -H github.com >> ~/.ssh/known_hosts
```

Now we configure Git for WSL:
1. Open Hyper, which should open `bash.exe` terminal
2. Generate another key `ssh-keygen`
3. Copy `~/.ssh/id_rsa.pub`
4. Add to permitted GitHub SSH keys in GitHub settings
5. Configure git:
```bash
# Add my custom GitHub configuration
./windows/link-gitconfig.sh
```
6. Finally add github.com to `known_hosts`:
```
ssh-keyscan -H github.com >> ~/.ssh/known_hosts
```

Done, now we can use Git with GitHub

## Oh my ZSH
Using Hyper (with Bash):

```
./windows/install-oh-my-zsh.sh
```

This will set up Oh My ZSH, which in my opinion is better than just pure Bash.

## Install Node
In Hyper (now ZSH)

```
./windows/install-node.sh
```

## Install Golang
In Hyper (now ZSH)

```
./windows/install-golang.sh
```

## Install Python
In Hyper (now ZSH)

```
./windows/install-python.sh
```

## Apple Magic Keyboard mappings
I use a Magic Keyboard to work and it was slowing me down a lot not to have the right mappings,
at least while I get used to the Windows shortcuts. Therefore I added a script to accelerate
the development while adapting.

To use just open the `magic-keyboard.ahk` file and it will open with AutoHotkey, which was
installed with Choco. To stop it, just close the program.