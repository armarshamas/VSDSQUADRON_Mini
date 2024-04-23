Task 1:
Install RISC-V GNU Toolchain 
![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/23158c82-c463-440f-9260-cc34f4fb5b1c)

install Yosys, iverilog, gtkwave

Yosys
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/a4c6dc0a-1e3b-41c0-b4f1-69a30904f848)

iverilog:
sudo apt-get install iverilog
![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/0bc2b5bd-a124-4416-bd97-86a692300c78)

gtkwave:
sudo apt update
sudo apt install gtkwave

![image](https://github.com/armarshamas/VSDSQUADRON_Mini/assets/73387351/8deb50fc-2602-47cd-a561-23c87864102f)

