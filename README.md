# ESP32 developer environment

## Vagrant

Vagrant machine password: vagrant


## Install developer environment on Ubuntu 20.04

Source of below instructions: https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/

### Prerequisities

```
sudo apt -y install git wget flex bison gperf cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0
sudo apt -y install python3 python3-pip python3-setuptools
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10
```

Execute:

`sudo usermod -a -G dialout $USER`

and after this log-out and log-in user.

Open Terminal, and run the following commands:

```
mkdir -p ~/esp
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
```

```
cd ~/esp/esp-idf
./install.sh
```

In the terminal where you are going to use ESP-IDF, run:

```
. $HOME/esp/esp-idf/export.sh
```

```
python -m pip install --upgrade pip
```

```
echo "alias get_idf='. $HOME/esp/esp-idf/export.sh'" >> ~/.bashrc
```

```
cd ~/esp
cp -r $IDF_PATH/examples/get-started/hello_world .
```

```
cd ~/esp/hello_world
idf.py set-target esp32s2
```

```
idf.py menuconfig
```

Build binary:
```
idf.py build
```

Flash to device:
```
idf.py -p /dev/ttyUSB0 flash
```


### Install VS Code

Source of instructions: https://code.visualstudio.com/docs/setup/linux

```
sudo apt -y install apt-transport-https
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
rm -f packages.microsoft.gpg

sudo apt update
sudo apt install code # or code-insiders
```

### Install VS Code ESP extension

Source of instructions:
https://github.com/espressif/vscode-esp-idf-extension/blob/master/docs/tutorial/install.md

https://github.com/espressif/vscode-esp-idf-extension/blob/master/README.md#Prerequisites

https://github.com/espressif/vscode-esp-idf-extension/blob/master/docs/SETUP.md

Open terminal and run:

```
get_idf
code
```

Launch VSCode Quick Open (<kbd>Ctrl</kbd>+<kbd>P</kbd>) and then paste the following command and press enter

    ext install esp-idf-extension

Click "install".

Important: Next open folder "~/esp/hello_world" (otherwise extension configuration will hang)

Open (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>) and type [configure esp-idf extension]. After, choose the ESP-IDF: Configure ESP-IDF extension option.

Then choose: Use existing setup

# Notes

```
Installing collected packages: filelock, distlib, appdirs, virtualenv
  WARNING: The script virtualenv is installed in '/home/vagrant/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
Successfully installed appdirs-1.4.4 distlib-0.3.2 filelock-3.0.12 virtualenv-20.4.7
WARNING: You are using pip version 20.2.4; however, version 21.1.3 is available.
You should consider upgrading via the '/usr/bin/python3 -m pip install --upgrade pip' command.
```
