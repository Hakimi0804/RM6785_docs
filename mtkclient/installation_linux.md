# Installation guide for Linux
Since there are a lot of Linux distros, we could not afford to make a guide for all of them. However, we made a guide for the most common ones.

### 1. Distro-specific step - Package installation
- Arch Linux

    Install the following packages:
    - git
    - python-pip
    - libusb
    - libpng12

    Run: `$ sudo pacman -Sy --needed --noconfirm git python-pip libusb libpng12`

- Fedora Linux

    Install the following packages:
    - git
    - python-pip
    - libusb
    - libpng12

    Run: `$ sudo dnf install -y git python-pip libusb libpng12`

- Ubuntu

    Install the following packages:
    - git
    - python-pip
    - libusb-1.0-0
    - libpng12-0

    Run:
    ```bash
    $ sudo apt update
    $ sudo add-apt-repository -y ppa:linuxuprising/libpng12
    $ sudo apt update
    $ sudo apt-get install -y libpng12-0 python3 python3-pip git libusb-1.0-0
    ```

## 2. Clone the repository
```bash
$ git clone https://github.com/bkerler/mtkclient
$ cd mtkclient
```

## 3. Install requirements
`$ pip3 install -r requirements.txt`

## 4. Optional: Build the tool
*This install mtkclient globally thus allowing you to use it from any directories without having to specify full path to the python script.*
```bash
$ python3 setup.py build
$ sudo python3 setup.py install
```

## 5. Install rules
```bash
$ sudo groupadd dialout
$ sudo groupadd plugdev
$ sudo usermod -a -G dialout,plugdev $USER
$ sudo cp Setup/Linux/*.rules /etc/udev/rules.d
$ sudo udevadm control -R
```

## 6. Done!
You might come here to do bypass, checkout [must knows](must-knows.md#bypass) to learn how. Be sure to read the rest of the must knows section ;)
