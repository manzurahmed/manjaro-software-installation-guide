# Install Composer and configure with XAMPP

Install composer like so:
```
sudo curl -s https://getcomposer.org/installer | /opt/lampp/bin/php
```

After installation, you should then symlink it by running command:
```
sudo ln -s /opt/lampp/bin/php /usr/local/bin/php
```

Then run the command below to allow the 'composer' command to be run globally (this will be run from within the folder where you've just installed composer in which a composer.phar file has just been created):
```
sudo mv composer.phar /usr/local/bin/composer
```

