# linux_tips
## some tips on using linux

To list all packages intentionally installed (not as dependencies) by apt commands, run the following :
```
(zcat $(ls -tr /var/log/apt/history.log*.gz); cat /var/log/apt/history.log) 2>/dev/null |
  egrep '^(Start-Date:|Commandline:)' |
  grep -v aptdaemon |
  egrep '^Commandline:'
```

## Audio CDs rippen und Player (Clementine / VLC):

https://wiki.ubuntuusers.de/AudioPlayer/

https://wiki.ubuntuusers.de/CDs_rippen/


## DVDs erzeugen mit devede: https://www.linux-community.de/ausgaben/linuxuser/2012/05/dvds-erzeugen-mit-devede/


## Autostart scripts under bodhi linux:

For a script that starts with moksha, there's ~/.e/e/applications/startup/startupcommands and you can put anything you want in there (create it if it doesnt exist).

## Mit IPhone verbinden: https://kmj.at/2018-05-12-Mit-Linux-IPhone-sichern-und-auf-Daten-zugreifen/

Im Terminal: apt-get install libimobiledevice6 libimobiledevice-utils libusbmuxd4 ifuse gvfs-fuse

IPhone mit USB Kabel anschliessen. IPhone entsperren.

Im Terminal: idevicepair pair

Computer vertrauen und Pin am IPhone eingeben.

Im Terminal: mkdir $HOME/iphone - nur 1x nötig = Mountpoint anlegen.

Im Terminal: ifuse $HOME/iphone - mounten

Im Terminal: fusermount -u $HOME/iphone - unmounten

Bei mir reichte es dann einfach im Filebrowser auf das angezeigte Iphone/Dokumente zu klicken. 
So kann man z.B voher vlc auf dem IPhone installieren und danach unter Dokumente VLC dann dateien aufspielen.


## Bluetooth Gerät verbinden:
```
You can try running bluetoothctl from the command line, make sure your device is on / ready to be discovered:

$ bluetoothctl
[NEW] Controller AA:BB:CC:DD:EE:FF device-name [default]
Any other bluetooth devices will be listed here. You'll then be inside a [bluetooth] prompt.

First, turn bluetooth power on (if your device is off):

[bluetooth]# power on
Changing power on succeeded
Then, make sure your agent is registered:

[bluetooth]# agent on
Agent registered

[bluetooth]# default-agent 
Default agent request successful
Now you can scan for devices from the console:

[bluetooth]# scan on
Discovery started
[CHG] Controller AA:BB:CC:DD:EE:FF Discovering: yes
[NEW] Device FF:EE:DD:CC:BB:AA Someone's Keyboard
You can manually pair from here as well:

[bluetooth]# pair FF:EE:DD:CC:BB:AA 
Attempting to pair with FF:EE:DD:CC:BB:AA 
[CHG] Device C8:E0:EB:04:52:55 Connected: yes
At this point, you should be prompted to enter a pin code for pairing:

Request PIN code
[agent] Enter PIN code: 12345
Enter a number (eg. 12345), and you will be prompted to input the same number from the device:

[Someone's Keyboard]# 12345
You should then be notified that your keyboard has paired:

[CHG] Device FF:EE:DD:CC:BB:AA Paired: yes
```

