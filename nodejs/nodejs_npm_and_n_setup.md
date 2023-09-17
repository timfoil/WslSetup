# Setup

### node and npm

``` bash
sudo apt install nodejs
sudo apt install npm
```

this installed node v12 (yikes very outdated we'll need to update) & npm v8.5.1 (probably outdated but I'm not super familiar with npm versioning)

### node package manager "n"

`npm install -g n`

this failed because you need sudo permissions to install to the default directory globally I think (tried doing it in random directory with -g and it works)

I want to have to avoid using sudo with npm install so I will do a workaround to prevent myself from having to do this

info is available here https://github.com/sindresorhus/guides/blob/main/npm-global-without-sudo.md
 but in case it gets changed or yoinked at some point...

1. create dir for global pkgs under home (`mkdir ~/.npm-packages`)
2. npm needs to know where to store these packages `npm config set prefix "~/.npm-packages"`
3. configure vars in .bashrc

#### .bashrc changes
``` bash
npm_package_path="${HOME}/.npm-packages"
export PATH="$PATH:$npm_package_path/bin"
export MANPATH="${MANPATH-$(manpath)}:$npm_package_path/share/man"
```

Not exactly sure how manpath is used but probably has to do with where man docs are installed by default

running `npm install -g n` now works!

ok so now for n setup, running `npm n 20` fails because it tries to install in `/usr/local` which it does not have permissions for due to lack of `sudo` (which I don't want to use)

to fix this we define `N_PREFIX` which `n` will use to determine where it can find/place node installations. We'll put this in a place we have permission to view and can easily find, `$HOME/.n`

#### Create the directory where we'll place n and its installations

``` bash
mkdir ~/.n
```

#### then update .bashrc 
``` bash
export N_PREFIX="$HOME/.n" #define N_PREFIX
export PATH="$N_PREFIX/bin:$PATH" #add the N_PREFIX dir to the front of our path so we can run n's current nodejs setting
```

The command  `n i 20` (n install node v20) now installs node v20.6.1 (latest version at this time of writing)

Check the version number of both node and npm to check that they are using the expected version

``` bash
node --version
npm --version
```

Now we can remove the original versions of nodejs and npm that we installed with apt. If we ever want those versions again we can just reinstall using n

``` bash
sudo apt purge node
sudo apt purge npm
sudo apt autoremove
```
