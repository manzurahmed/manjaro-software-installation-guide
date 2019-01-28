# Download Xampp from Official Website

1. Download "Xampp for Linux" from ApacheFriends website: https://www.apachefriends.org/download.html
2. Check this Linux FAQ for installation guidelines: https://www.apachefriends.org/faq_linux.html

# Install Xampp on Manjaro

Issue the following two commands to start the automated installer.

```
chmod 755 xampp-linux-*-installer.run
sudo ./xampp-linux-*-installer.run
```

That's all. XAMPP is now installed below the /opt/lampp directory.

# Autostart Xampp on boot in Manjaro Linux

Following this tutorial: https://wiki.archlinux.org/index.php/XAMPP

In order to start Xampp at boot, create a systemd service for it (/etc/systemd/system/xampp.service):

First, create a file, named, xampp.service:

```
sudo touch xampp.service
sudo vim xampp.service
```

Paste the following lines in the file, save and exit.

```
[Unit]
Description=XAMPP

[Service]
ExecStart=/opt/lampp/lampp start
ExecStop=/opt/lampp/lampp stop
Type=forking

[Install]
WantedBy=multi-user.target
```
Make the file "executable".
```
chmod a+x xampp.service
```

**Need to test**: Enable a unit to be started on bootup and Start immediately:
```
systemctl enable --now unit
```


All set! Restart your PC, open your browser, type "http://localhost/" in the addressbar. You should see the content from your local webserver's DocumentRoot.

### Start xampp manually
```
systemctl start xampp.service
```

## How to SOLVE phpMyAdmin Error (The $cfg[‘TempDir’] (./tmp/) is not accessible.)

Create a folder "tmp" in "/opt/lampp/phpmyadmin" folder. The path should be "/opt/lampp/phpmyadmin/tmp".

Open "config.inc.php" file that is found in /opt/lampp/phpmyadmin folder and add the following line:

```
sudo vim config.inc.php
```

```
$cfg['TempDir'] = "/opt/lampp/phpmyadmin/tmp";
```

Save the file. Give "write" permission (0777) to everybody.

```
sudo chmod a+w tmp
```

Thus, the error message will be solved.

## Running apache (httpd) process under the user account

If you want to ensure that you do not face any further permission related issue while running and customizing XAMPP web server, you should run apache process under your own user account. This simple fix removes several permission related issues.

For this, we have to modify the /opt/lampp/etc/httpd.conf file. Before we modify this file, let’s take the backup of current file.

```
sudo cp /opt/lampp/etc/httpd.conf /opt/lampp/etc/httpd.conf.bak
ls /opt/lampp/etc/httpd*
```

Now open this file for editing
```
sudo gedit /opt/lampp/etc/httpd.conf
```

Now locate following directives

```
User daemon
Group daemon
```

Replace **daemon** value with your username and group name and save the file:

```
User manzur
Group manzur
```

Once file is saved, restart the XAMPP and verify that all services are started properly
