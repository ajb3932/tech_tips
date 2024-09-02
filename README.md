# Intro
Handy Hints and Tips that I have found useful

## #01 Windows

### 01-001 Disable Hybernate (saves space on C: drive)
```powercfg.exe /hibernate off```

### 01-002 Allow Extentions in locked down Chromium Browsers (Edge, Chrome, Brave)
- Registry Key: ```HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge\ExtensionInstallForcelist```
- String Value: ```1``` or the n+1 of the extentions currently installed
- String Data: ```your_extention_key``` eg ```jbkfoedolllekgbhcbcoahefnbanhhlh```

## #02 Linux

## 02-001 Docker Easy Install
Install docker and add user to group:
```sh -c "$(curl -fsSL https://get.docker.com)" && sudo usermod -aG docker $USER```

## 02-002 Managing Users
<p id="bkmrk-add-new-user">Add New User</p>
<pre id="bkmrk-sudo-useradd--m--g-s"><code class="language-bash">sudo useradd -m -g sudo -s /bin/bash alex
echo "alex ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/alex
sudo passwd alex</code></pre>
<p id="bkmrk-disable-root">Disable Root</p>
<pre id="bkmrk-%27s%2Froot%3A%5C%2Fbin%5C%2Fbash%2F"><code class="language-bash">sudo sed -i 's/root:\/bin\/bash/root:\/usr\/sbin\/nologin/' /etc/passwd</code></pre>
<p id="bkmrk-securing-ssh">Securing SSH</p>
<pre id="bkmrk-sudo-sed--i-%27s%2F%23perm"><code class="language-bash">sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo systemctl restart sshd</code></pre>
<p id="bkmrk-%C2%A0"></p>
<p id="bkmrk-"></p>

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
