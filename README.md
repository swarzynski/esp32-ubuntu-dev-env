# DataLogger

## Install developer environment on Ubuntu 20.04

### Prerequisities

```
sudo apt -y install git wget flex bison gperf cmake ninja-build ccache libffi-dev libssl-dev dfu-util
sudo apt -y install python3 python3-pip python3-setuptools python3-venv
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10
```

Open Terminal, and run the following commands:

```
mkdir -p ~/esp
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
```

Execute:

`sudo usermod -a -G dialout $USER`

and after this log-out and log-in user.


```
cd ~/esp/esp-idf
./install.sh
```

In the terminal where you are going to use ESP-IDF, run:

```
. $HOME/esp/esp-idf/export.sh
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
idf.py menuconfig
```

```
idf.py build
idf.py -p /dev/ttyUSB0 flash
```




### Install VS Code

`sudo snap install code --classic`


#### Bugfix

It seems that to successfully install ESP extension you need to run:

`pip install psutil requests typing xmlrunner`


Optional:
```
pip install pyserial future pyparsing pyelftools gdbgui pygdbmi kconfiglib reedsolo bitstring ecdsa
```



otherwise will be errors.

#### Install and configure ESP extension

Launch VSCode Quick Open (<kbd>Ctrl</kbd>+<kbd>P</kbd>) and then paste the following command and press enter

    ext install esp-idf-extension

Click "install".

Then I suppose these steps:
https://github.com/espressif/vscode-esp-idf-extension/blob/master/docs/ONBOARDING.md#directly-modify-settingsjson

```
.:/usr/bin:/home/adrian/.espressif/tools/xtensa-esp32-elf/esp-2020r3-8.4.0/xtensa-esp32-elf/bin:/home/adrian/.espressif/tools/xtensa-esp32s2-elf/esp-2020r3-8.4.0/xtensa-esp32s2-elf/bin:/home/adrian/.espressif/tools/esp32ulp-elf/2.28.51-esp-20191205/esp32ulp-elf-binutils/bin:/home/adrian/.espressif/tools/esp32s2ulp-elf/2.28.51-esp-20191205/esp32s2ulp-elf-binutils/bin:/home/adrian/.espressif/tools/openocd-esp32/v0.10.0-esp32-20200709/openocd-esp32/bin:/home/adrian/.espressif/tools/xtensa-esp32s3-elf/esp-2020r3-8.4.0/xtensa-esp32s3-elf/bin/
```

```
/home/adrian/.espressif/tools/openocd-esp32/v0.10.0-esp32-20200709/openocd-esp32/share/openocd/scripts
```
