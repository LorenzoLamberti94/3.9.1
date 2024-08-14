# install

## Prerequisites 

#### OS and gcc version
```
Ubuntu 20.04.6 LTS
gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.2) 
```

#### Conda

create a conda environment (and call it gap_sdk) to install all the packets needed by the sdk (pip commands below)

```
conda create --name gap_sdk python==3.6.10 numpy cython
conda activate gap_sdk
```

#### packages for the sdk

```
sudo apt-get install -y build-essential git libftdi-dev libftdi1 doxygen python3-pip libsdl2-dev curl cmake libusb-1.0-0-dev scons gtkwave libsndfile1-dev rsync autoconf automake texinfo libtool pkg-config libsdl2-ttf-dev
```

#### Opencv3.2

Unfortunately it is not ufficially supported anymore. But here's how to install it

this is a repo that allows to do so: https://gist.github.com/syneart/3e6bb68de8b6390d2eb18bff67767dcb 
To install execute the following

```
# wget -O - https://gist.githubusercontent.com/syneart/3e6bb68de8b6390d2eb18bff67767dcb/raw/OpenCV3.2withContrib.sh | bash
```

check if installed correctly:
```
 dpkg -l | grep libopencv
```

## Install Toolchain

```
cd ~/gap_riscv_toolchain
./install.sh
	if you chose a custom path for install, add this to your .bashrc file:
	export GAP_RISCV_GCC_TOOLCHAIN="custom/path/that/you/chose"
```


## Install GAP SDK

```
cd gap_sdk
source gap_sdk/config/ai_deck.sh
pip install -r requirements.txt
cd tools/nntool/
pip install -r requirements.txt
cd ../..
make sdk
```
## source sdk

```
source source_3.9.1.sh
```

note: change absolute paths in source_3.9.1.sh according to your setup

## TEST: To check everything works

```
cd examples/pmsis/helloworld
make clean all run platform=board
```
