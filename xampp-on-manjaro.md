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

All set! Restart your PC, open your browser, type "http://localhost/" in the addressbar. You should see the content from your local webserver's DocumentRoot.

### Start xampp manually
```
systemctl start xampp.service
```
