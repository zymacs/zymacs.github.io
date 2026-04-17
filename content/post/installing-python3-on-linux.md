---
title: Installing python3 on Linux
date: 2026-03-04
tags:
  - "python"
  - "python3"
  - "development"
categories:
  - "Development"
  - "Python3"
---


Python comes pre-installed on most Linux distros. But if for whichever reason it isn't installed on yours, here's how to fix that; 

First, let's update and upgrade your system

If you are on Ubuntu, run:

```
 sudo apt update && sudo apt upgrade
```

For Arch, run: 

```
sudo pacman -Syu
```

Fedora: 

```
sudo dnf upgrade
```

Now let's install python (plus some extra packages you will most definitely eventually need when using python)

Ubuntu

```
sudo apt install python3 python3-pip python3-venv
```

Arch

```
sudo pacman -S python python-pip python-virtualenv
```

Fedora

```
sudo dnf install python3 python3-pip python3-virtualenv python3-devel
``` 

Regardless of which distro you are running, confirm python is installed by running

```
python --version
```

If that command runs successfully (prints out what python version is installed) then you are ready to run python programs on your system. 

Should you face any errors, it surely is the case someone has faced them before online and they got the answer posted. If that does not help, please drop your issue in the comment section and someone , including me, could provide you with assistance.

Hope that helped. Happy Hacking. 


 


 
