# Setup

Relatively simple, went to https://getcomposer.org and found some instructions on how to install.

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'e21205b207c3ff031906575712edab6f13eb0b361f2085f1f1237b7126d785e826a450292b6cfd1d64d92e6563bbde02') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

It places a composer.phar file in the directory you run the installer in. Installing is usually done per repo/directory. 

I wanted to install globally, to do that you just add the dir you installed in (added composer.phar to) to your PATH.

I placed mine in `~/bin` (which I created, idk if this kind of setup is standard or not)

**edit:** I moved this to `/usr/local/bin` which is conventionally the typical place for users/admin to install software system-wide. Typically `~/.local/bin` is the convention used for per-user installations (this isn't part of PATH by default though so needs to be added). Also note that files in `/usr/local/bin` typically have root as the owner and group. So run `chgrp root composer` and `chown root composer`, it also should be set to have 755 permissions but that was already taken care of for me. (Actually it looks like both `~/.local/bin` and the dir `~/bin` are conditionally added to `$PATH` in `~/.profile` on my installation by default so `$HOME/bin` may be a typical appropriate alternative installation directory) 

rename composer.phar to just composer (aka `mv composer.phar composer`) you invoke composer with `php composer.phar` but there is a shebang by default in the file to run with php so we can now just use `composer` anywhere as we please