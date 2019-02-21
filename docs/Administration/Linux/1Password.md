#1Password on Linux and support Web Browser Extension

##Install [1Password for Windows](https://c.1password.com/dist/1P/win4/1Password-4.6.2.626.exe) in Wine
```
$ wine 1Password-4.6.2.626.exe
```
Select the default install location: `c:\Program Files (x86)\1Password 4`.

##Run 1Password and Agent
```
$ wine ~/.wine/drive_c/Program\ Files\ \(x86\)/1Password\ 4/1Password.exe

$ wine ~/.wine/drive_c/Program\ Files\ \(x86\)/1Password\ 4/Agile1PAgent.exe
```

Or better with the run 1Password agent with systemd when logging. Create a user systemd unit, let's call it `1Password.agent.service`.
```
$ nano $HOME/.config/systemd/user/1Password.agent.service
```
Paste the following content into `1Password.agent.service`
```
[Unit]
Description=1Password agent
After=display-manager.service

[Service]
ExecStart=/usr/bin/wine ".wine/drive_c/Program Files (x86)/1Password 4/Agile1pAgent.exe"
Restart=always
Environment=DISPLAY=:0

[Install]
WantedBy=default.target
```

```
# Edit it later with systemd command systemctl
$ systemctl --user edit --full 1Password.agent.service

# Check service status
$ systemctl --user status 1Password.agent.service
```

##Then in 1Password, disable “Verify web browser code signature”, from menu `Help -> Advanced -> Verify web browser code signature`

##You can download Google Chrome extension
[1Password extension (desktop app required)](https://chrome.google.com/webstore/detail/1password-extension-deskt/aomjjhallfgjeglblehebfpbcfeobpgk?hl=en)

##Firefox extension
[1Password extension (desktop app required)](https://1password.com/browsers/beta/firefox/), tested on Firefox v56 (last version before Firefox Quantum) or v65.0. Not working as the button is greyed out.

##Restart your browser and it should work.
And there you have it…


------------------------------------------------------------------------
Inspired by [Install 1Password & browser agent with wine on Linux](https://blog.arkey.fr/2015/11/16/1Password-wine/) 