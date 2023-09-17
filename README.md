# About
Notes on what I did to setup wsl (and various technologies) on my computer so if I have to do it again quickly... I can do it again quickly. (Also keep track of what has been installed)

## General notes on installation conventions

Typically `~/.local/bin` is the convention used for per-user installations (this sometimes isn't part of PATH by default though so needs to be added) whereas `/usr/local/bin` is used as a system-wide installation directory. (Actually it looks like both `~/.local/bin` and the dir `~/bin` are conditionally added to `$PATH` in `~/.profile` on my installation by default so `$HOME/bin` may be a typical appropriate alternative installation directory)

Also note that files in `/usr/local/bin` typically have root as the owner and group with permissions set to 755. So run `chmod 755 <software-being-installed>` then `chgrp root <software-being-installed>` and `chown root <software-being-installed>` after adding things there generally.