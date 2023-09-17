# setup

php can be installed on ubuntu by default with `apt` but the default php version is 8.1 and the current version is 8.2 which is a minor version ahead.

In order to install the current version of php I had to add another repository to apt. `sudo add-apt-repository ppa:ondrej/php ` 

I'm not a big fan of this because it's literally maintained by some guy, but I did this anyways because 
- instructions on how to download and install php otherwise are scarce 

- I looked into manually downloading php from php.net and a tar.gz file is provided with some confusing blurbs about apache/nginx which I think are addons 
    - there weren't really detailed instuctions & I'm not sure about the typical way of installing things on ubuntu besides just adding things to PATH 
    - I figured I'd probabably mess it up doing it on my own without more guidance
    - I could not find any resources that reccomended downloading php this way
- most/all resources pointed me towards installing this way and I'd rather not do a custom install when I don't really know best practices for locations/permissions/setup
- this repository has been around for a long time and most online resources were touting it's efficacy & trustworthiness


Not great reasons I know, but I wanted something standard, easy, and well-documented for setup instead of doing something I might have to fiddle with.


```
sudo add-apt-repository ppa:ondrej/php

sudo apt update

# the names in the curly brackets will become php8.2-bz2 php8.2-curl php8.2-mbstring etc...  
sudo apt install php8.2 php8.2-cli php8.2-{bz2,curl,mbstring,intl,common,fpm,mysql,zip,gd,xml,bcmath,common}
```