
# mac-gestures

### 1. Clone xSwipe

    git clone git@github.com:arunhedcet/mac-gestures.git
    
### 2. Install X11::GUITest

To install libx11-guitest-perl from synaptic package manager
Or run the script on the terminal run as

    $ sudo apt-get install libx11-guitest-perl
    
Install smart-comments perl module

    git clone git@github.com:gitpan/Smart-Comments.git
    cd Smart-Comments
    perl Makefile.PL
    make
    make test
    sudo make install

---
#### NOTE: If using Ubuntu14.04, or later
##### Install older version synaptics driver that is compatible with xSwipe.

```bash
$ sudo apt-get install -y git build-essential libevdev-dev autoconf automake libmtdev-dev xorg-dev xutils-dev libtool
$ sudo apt-get remove -y xserver-xorg-input-synaptics
$ git clone https://github.com/Chosko/xserver-xorg-input-synaptics.git
$ cd xserver-xorg-input-synaptics
$ ./autogen.sh
$ ./configure --exec_prefix=/usr
$ make
$ sudo make install
```
---

### 3. Enable SHMConfig

Open /etc/X11/xorg.conf.d/50-synaptics.conf with your favorite text editor and edit it to enable SHMConfig

    $ sudo gedit /etc/X11/xorg.conf.d/50-synaptics.conf

**NOTE**:You will need to create the /etc/X11/xorg.conf.d/ directory and create 50-synaptics.conf if it doesn't exist yet.
     `$ sudo mkdir /etc/X11/xorg.conf.d/`

##### /etc/X11/xorg.conf.d/50-synaptics.conf

    Section "InputClass"
    Identifier "evdev touchpad catchall"
    Driver "synaptics"
    MatchDevicePath "/dev/input/event*"
    MatchIsTouchpad "on"
    Option "Protocol" "event"
    Option "SHMConfig" "on"
    EndSection

To reflect SHMConfig, restart your session.

##### copy gestures.sh  to /etc/profile.d

    sudo cp gestures.sh /etc/profile.d/
    
    
Thanks to [iberianpig](https://github.com/iberianpig) for the xSwipe module
