# wsl-install-guide

## Install WSL
Step 1 from: 

https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-1---enable-the-windows-subsystem-for-linux

## Install WSL2
Step 3 onward:

https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-3---enable-virtual-machine-feature

`NOTE: you will need to restart before step 4!`

## Pick your distro
I recommend Ubuntu 20.04 LTS

https://www.microsoft.com/en-ca/p/ubuntu-2004-lts/9n6svws3rx71?rtc=1#activetab=pivot:overviewtab

## Install OC
* Download this asset tar by clicking the link

https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz

Our linux subsystem is a different volume so we need to transfer the binary there
* Start your WSL terminal, and in the terminal, run:

`cp /mnt/c/Users/<YOURUSER>/Downloads/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz .`

`tar -xvf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz`

`cd openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/ && mv oc /usr/bin/`

## Install Docker
* Ensure the WSL engine config is enabled in docker desktop for windows:
https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers#install-docker-desktop
* You may need to grant sudo to docker

## Install Make
`sudo apt-get install make`

## Extras:
* want to not copy your windows source files? use a soft link to your src in the windows volume:
`ln -s mnt/c//Users/<SRCLOCATION> windowsfiles`

* SSH Keys: WSL uses its own SSH agent, you can copy your windows ssh key by using `cp` like in the oc step, and moving them to a `~/.ssh` directory