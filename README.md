# MANUS Core Integrated SDK Installation Guide
This project is Python API for MANUS Core 3.1. We follow the adaption in [Bidex_Manux_Teleop](https://github.com/leap-hand/Bidex_Manus_Teleop).

## Installation

1. Install [cppzmq](https://github.com/zeromq/cppzmq/tree/master).
    ```bash
    sudo apt-get install libzmq3-dev
    git clone git@github.com:zeromq/cppzmq.git
    cd cppzmq
    mkdir build
    cd build
    cmake ..
    sudo make -j4 install
    ```

2. Install MANUS Core Integrated SDK

- Install required packages.
    ```bash
    sudo apt-get update && sudo apt-get install -y build-essential libusb-1.0-0-dev libudev-dev gdb libncurses5-dev && sudo apt-get clean
    ```

- Install udev rules.
    ```bash
    sudo cp ./useful_files/70-manus-hid.rules /etc/udev/rules.d/
    sudo udevadm control --reload-rules && sudo udevadm trigger
    ```

- Copy `SDKClient_Linux/ManusSDK/lib/libManusSDK_Integrated.so` from the offcial SDK (you can also download it from [here](https://drive.google.com/file/d/1zMkH40ndV10q5fFWzOPQXwjWkp026bLv/view?usp=drive_link)) and place it to `SDKClient_Linux/ManusSDK/lib/libManusSDK.so`.

- Build the SDK.
    ```bash
    cd SDKClient_Linux
    make all
    ```

- The output `SDKClient_Linux.out` is the target SDK.

## Usage
To use the SDK, run
```bash
./SDKClient_Linux.out
```

`python/minimal_example.py` provides an example to receive the glove data.