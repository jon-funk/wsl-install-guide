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

v3
https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz

v4
https://github.com/openshift/okd/releases/download/4.6.0-0.okd-2021-02-14-205305/openshift-client-linux-4.6.0-0.okd-2021-02-14-205305.tar.gz

Our linux subsystem is a different volume so we need to transfer the binary there
* Start your WSL terminal, and in the terminal, run:

`cp /mnt/c/Users/<YOURUSER>/Downloads/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz .`

`tar -xvf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz`

`cd openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/ && sudo mv oc /usr/bin/`

## Install WSL vscode plugin
* Install WSL plugin for vscode


https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl

## Install Docker
* Ensure the WSL engine config is enabled in docker desktop for windows:
https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers#install-docker-desktop
* You may need to grant sudo to docker
`sudo usermod -aG docker $USER`

`Note: Kill the WSL terminal and restart it so permissions are applied to the new session`

## Install Make
`sudo apt-get install make`

## Extras:
* want to not copy your windows source files? use a soft link to your src in the windows volume:
`ln -s mnt/c/Users/<SRCLOCATION> windowsfiles`

* SSH Keys: WSL uses its own SSH agent, you can copy your windows ssh key by using `cp` like in the oc step, and moving them to a `~/.ssh` directory with `mv`

* Disable bell via https://stackoverflow.com/a/36726662 steps 1 & 2 in most cases