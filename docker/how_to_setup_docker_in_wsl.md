# setup

Docker in WSL is pretty much already setup out of the box if you have docker-desktop in windows. You may need to enable it for the distro you are using though. 

If you have docker desktop running, go to the dashboard and then select the gear (for options) at the top of the dashboard in the sidebar  `resources > wsl integration`. Click the checkbox and/or enable the distros you want docker desktop to be able to power.

I saw whisperings of possibly dated info related to docker not being able to be installed by default inside wsl due to systemd not existing in wsl containers. The workaround being enabling systemd through the wsl.config file under `/etc/`. Don't do this, just follow the instructions above.