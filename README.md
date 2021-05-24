# PORTING vsomeip3 on QNX 7.0


## Dependencies

- **boost 1.55.0**：https://sourceforge.net/projects/boost/files/boost/1.55.0/
- **vsomeip 3.1.20**：https://github.com/bonewell/vsomeip.git

## Source Environment

```bash
source ~/qnx700/qnxsdp-env.sh
```

## Build Boost 1.55.0

```bash
tar -xvf boost_1_55_0.tar.gz
cd boost_1_55_0
patch -p1 < ../boost-1_55-qnx700.patch
./bootstrap.sh
./b2 install link=static toolset=qcc cxxflags="-Vgcc_ntox86_64" target-os=qnxnto --prefix=/home/lxl/work/SOALibrary/external/boost
```

## Build vsomeip 3.1.20

```bash
git clone git@github.com:lixiaolia/vsomeip-qnx.git
cd vsomeip-qnx
mkdir build && cd build
cmake -DCMAKE_TOOLCHAIN_FILE=../qnx_7.0.0_linux_x86_64.cmake -DCMAKE_INSTALL_PREFIX=/home/lxl/work/vsomeip-qnx/install ..
```



