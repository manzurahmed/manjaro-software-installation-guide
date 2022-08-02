# Download Xampp from Official Website

1. Download "Xampp for Linux" from ApacheFriends website: https://www.apachefriends.org/download.html
2. The downloaded file will be saved on the default save folder of your browser. In my case, it saved on "Desktop" under my "Home" folder. The filename was **xampp-linux-x64-7.4.1-1-installer.run**.

**N.B.** Check this Linux FAQ for installation guidelines: https://www.apachefriends.org/faq_linux.html

# Install Xampp on Manjaro

1. Open Terminal. Navigate to "Desktop" folder.
2. Issue the following two commands to start the automated installer.

```
chmod 755 xampp-linux-*-installer.run
sudo ./xampp-linux-*-installer.run
```

3. After a brief while, Xampp installer will pop up on the screen. Follow the instructions of the installer.

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

**Start the service at Startup**:

Enable a unit to be started on bootup and Start immediately:
```
systemctl enable --now xampp.service
```

All set!
- Restart your PC.
- Open your browser, type "http://localhost/" in the addressbar. You should see the content from your local webserver's DocumentRoot.

### Start xampp manually
```
systemctl start xampp.service
```

## How to SOLVE phpMyAdmin Error (The $cfg[‘TempDir’] (./tmp/) is not accessible.)

Create a folder **tmp** in **/opt/lampp/phpmyadmin** folder. The path should be "/opt/lampp/phpmyadmin/tmp".

Open "config.inc.php" file that is found in /opt/lampp/phpmyadmin folder and add the following line:

```
sudo vim config.inc.php
```

```
$cfg['TempDir'] = "/opt/lampp/phpmyadmin/tmp";
```

Save the file.

Give "write" permission (0777) to everybody.

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

Now open httpd.conf file for editing:
```
sudo vim /opt/lampp/etc/httpd.conf
```

Search for the following directives:

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

# Permission Issue

I encounter permission issue while creating any file or folder in **htdocs** folder. This folder is located in **/opt/lampp/** folder.. It is because, **htdocs** folder is owned by **root** user and group. My username (webtechriser) does not have root privilege. To solve the permission issue, I shall **change ownership** of the whole **htdocs** folder. Open up a Terminal and issue the following command:
```
sudo chown -R webtechriser:webtechriser htdocs
```
My username is now have read, write and delete privilege.

# XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system

I encountered this issue and after some Google, I found the solution at this link:

Source:
https://stackoverflow.com/questions/71299408/xampp-is-currently-only-availably-as-32-bit-application-please-use-a-32-bit-com

To solve this go to package manager and search for this package **libxcrypt-compat** then install it.
That's all, xampp will work fine
