# Intro
Handy Hints and Tips that I have found useful

## #01 Windows

### 01-001 Disable Hybernate (saves space on C: drive)
```powershell
powercfg.exe /hibernate off
```

### 01-002 Allow Extensions in locked down Chromium Browsers (Edge, Chrome, Brave)
- Registry Key: ```HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge\ExtensionInstallForcelist```
- String Value: ```1``` or the n+1 of the extensions currently installed
- String Data: ```your_extension_key``` eg ```jbkfoedolllekgbhcbcoahefnbanhhlh```

## #02 Linux

## 02-001 Docker Easy Install
Install docker and add user to group:
```bash
sh -c "$(curl -fsSL https://get.docker.com)"
sudo usermod -aG docker $USER
```

## 02-002 Managing Users
**Add New User** \
(This will add a new user with SUDO permissions and will not need to enter a password when excalating use with caution!)
```bash
sudo useradd -m -g sudo -s /bin/bash alex
echo "alex ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/alex
sudo passwd alex
```
**Disable Root**
```bash
sudo sed -i 's/root:\/bin\/bash/root:\/usr\/sbin\/nologin/' /etc/passwd
```
**Securing SSH**
```bash
sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo systemctl restart sshd
```

## 02-003 Convert RSA Private key to OpenSSH Key
```bash
ssh-keygen -p -N "" -f /path/to/key
```

## #03 Miscellaneous
### 03-001 Virus Total Query
```tag:known-distributor type:peexe microsoft:clean signature:"Microsoft Corporation"```

### 03-002 Remove Empty Lines VS Code
- Open Find menu
- Command + F on Mac
- Ctrl + F on Windows
- In the find box type: ```^(\s)*$\n```
- Leave the replace box empty
- Select 'Use Regular Expression'
- Select 'Replace All' button 
