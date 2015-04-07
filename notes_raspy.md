 * sudo apt-get install console-data
 * sudo dpkg-reconfigure --priority=low xserver-xorg
 * sudo dpkg-reconfigure --priority=low console-data
 * sudo dpkg-reconfigure locales
 * locale -a
 * sudo dpkg-reconfigure keyboard-configuration
 * Validate: sudo nano /etc/default/keyboard
 * invoke-rc.d keyboard-setup start
 * sudo vi /etc/vim/vimrc
 * sudo raspi-config
 * Setting locale:
    dpkg-reconfigure locales

 * Lost password: run `sudo raspi-config`
 * Lost root password: edit /etc/passwd, delete 'x' in root:x:...
 
 `shell
 sudo apt-get install vim

--
# Installing Kodi
[Raspian](http://michael.gorven.za.net/)

sudo vi /etc/apt/sources.list.d/mene.list
* add 'deb http://archive.mene.za.net/raspbian wheezy contrib' to it
### Import the archive signing key
sudo usermod -a -G tty pi
adding an existing user to a group; use 'id pi' to get groups. check /etc/groups for all groups

--
# Setting R in Ubuntu (may not work for me but useful for firewall)
[Ubuntu R install]i://r-interface.blogspot.com/2012/04/install-r-jgr-and-deducer-in-ubuntu.html)

- In .Rprofile or .Renviron:
  local({
  	Sys.setenv(http_proxy="http://username:password@tcdproxy.tcd.ie:8080")
	})
- Has additional info on Desktop icon + java + package with repo option

--
# Raspberry + R for GPIO temperature sensing
[Google Plus Blog](https://plus.google.com/+StephenBecker/posts/gSQB3M6cph7)

--
# OneDrive setup
[github](https://github.com/xybu/onedrive-d)
* Requires installation of pip for python3, apt-get install python3-pip, but cannot run it.
* Github install & setup was OK 
* Issues with starting it up
	* PYTHONPATH=/home/pi/bin/onedrive-d onedrive-d 
	* onedrive-pref is installed in /local/something... but needs path to od_pref


--
# grip to convert markdown to html
[Github for Grip](
[Raspberry for R](http://www.r-bloggers.com/fun-with-the-raspberry-pi/)
[WiringPi](https://projects.drogon.net/raspberry-pi/wiringpi/)

--
# VIM
 !mkdir ~/.vim/colors
 !cp $VIMRUNTIME/colors/morning.vim ~/.vim/colors/mine.vim

--
## Upgrading R from 2.15 to 3.0 in Raspbian
[Ref rblogger](http://www.r-bloggers.com/upgrade-and-update-r-2-15-to-r-3-0-in-debian-wheezy/)

* In /etc/apt/sources.list:
	R BACKPORTS FOR WHEEZY
	deb http://cran.revolutionanalytics.com/bin/linux/debian wheezy-cran3/
	#deb-src http://cran.revolutionanalytics.com/bin/linux/debian wheezy-cran3/

* Move library folder: $ mv ~/R/xx/2.15 ~/R/xx/3.0 
* In R (run as sudo):
	$ sudo R > update.packages(checkBuilt=TRUE, ask=FALSE) 

> The Debian backports archives on CRAN are signed with the key ID 381BA480, to add them, in a Terminal prompt type:

	gpg --keyserver pgp.mit.edu --recv-key 381BA480
	gpg -a --export 381BA480 > jranke_cran.asc
	sudo  apt-key add jranke_cran.asc

* FOURTH PART: UPDATE AND UPGRADE R:

> Save the file and you can either enter to Synaptic, update the packages list and then just upgrade the packages or in a terminal type:

	sudo apt-get update
	sudo apt-get upgrade

* But somehow the output does not work. I still get 2.15 when I run $ R
pi@raspberrypi ~/R $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  r-base r-base-dev r-cran-boot r-cran-codetools r-recommended
  The following packages will be upgraded:
    cups-bsd cups-client cups-common libcups2 libcupsimage2 r-base-html
	  r-doc-html
	  7 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
	  Need to get 2,280 kB of archives.
	  After this operation, 407 kB of additional disk space will be used.
	  Do you want to continue [Y/n]?


* Read this for 'kept back' packages: http://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it
* Reinstall R from source: http://stackoverflow.com/questions/28309891/install-r-3-1-2-on-wheezy-7-8-raspbian-fails 
* Above link also has option of upgrading wheezy to jesse debian OS with one apt src change
* Try that if nothing else works. https://sites.google.com/site/onmyraspberrypi/instal-pi/jessie


For Dropbox nautilus source compile: $ sudo apt-get install libnautilus-extension-dev
--
* Commands for Raspberry Pi:

- `cat /proc/version`
- `cat /proc/cpuinfo`
- `cat /proc/meminfo`
- `cat /proc/partitions` # reveal size and number of SD card partitions
- `vcgencmd measure_temp` 
- `free -o -h` # free system memory
- `lsusb`
- `sudo raspi-config`
- `sudo shutdown -h 21:55`

--
# How to start X-windows export 
[Ref](http://www.ece.unm.edu/csg/email/XServer_Putty_Windows7-ECE.pdf)

- Putty, set Config > SSH > X11 > PortForwarding Yes
- Download [xming](http://sourceforge.net/projects/xming/) - choose do not install ssh client option
- Make sure /etc/ssh/sshd-config has X11 Port Forwarding = Yes
- That is it!


# IPython Server

[Ref](https://arundurvasula.wordpress.com/2014/04/01/remote-ipython-notebook-with-raspberry-pi/)

# Installed scikit-learn 
Based on linux instructions on the site.  Lots of apt-get install


# Github .vim install
[Ref](http://gregwoods.co.uk/2014/01/syntax-highlighting-in-vim-on-a-remote-raspberrypi/)
cd ~
mv .vimrc .vim/.vimrc
ln -s .vim/.vimrc .vimrc
cd .vim
git init
ls -la         (shows hidden files)

Configure GIT
git config --global user.name "your full name"
git config --local user.name "your full name"
git config --global user.email "your email id"
git config --local user.email "your email id"
git config -l
still in the ~/.vim folder…

git add .
git commit -m "Initial commit of my vim configuration"
git remote add origin https://github.com/GregWoods/.vim

//had to do a git pull first
git pull https://github.com/GregWoods/.vim
git push origin master
 

 My VIMconfiguration is now on github.
To install my Vim Config onto a new server…
cd ~
git clone https://github.com/GregWoods/.vim.git .vim
ln -s .vim/.vimrc .vimrc
