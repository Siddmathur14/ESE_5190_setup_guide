# Setting up WSL , NeoVim and PuTTY

# WSL 
 - First we install the *Windows Susbsytem for Linux* which is a feature of the Windows operating system that allows you to run a Linux system along with Linux command- line tools , directly on windows. I will be using NeoVim as my text editor.
- To begin with , we enable the *Windows Subsystem for Linux* in the windows features.
- You will be required to reboot and restart your system for the changes to reflect.
- I installed Debian from the microsoft store because I had problems installing Ubuntu due to an older version of Windows.
- You will be required to setup a username and password to proceed.
- Post this , update your system using the following command:
 <br> ``` $ sudo apt update && sudo apt upgrade```
 
 # NeoVim
 - First off , we have to download the *build- essential* package from Ubuntu's repository to install the packages required for building the software. Run the following command to do so:
 <br> ``` $ sudo apt install build-essential```
 - Now we can proceed to installing Neovim for which we can access the latest release of NeoVim from its github repository. Look for the file ```nvim-linux64.deb```.
 - Download this file to your WSL and place it in your downloads drive.
 - Now we can install it using the following command :
 <br> ``` $ sudo apt install ./nvim-linux64.deb```
 - This completes the installation process of NeoVim

# PuTTY
- I already had MobaXterm installed which consists of an inbuilt PuTTY and that can be used as a serial console. You can easily install the free version of MobaXterm online.

# Pico-SDK Setup
- We start off with cloning the ```pico-sdk``` and ```pico-examples``` repository to our local machine.  
- Run the following command to install the dependencies : 
<br> ```$ sudo apt install build-essential cmake gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib```

![embedded setup5](https://user-images.githubusercontent.com/114244849/194979720-b53d51f6-8455-4ade-aa37-83f6af1bfde6.JPG)

- Then we will need to install git on our machine using the command: `$ sudo apt install git`
- Run the following commands to navigate to your `home` directory and to clone the required repositories:
<br>

```$ mkdir pico
$ cd ./pico
$ git clone -b master https://github.com/raspberrypi/pico-sdk.git
$ cd ./pico-sdk
$ git submodule update --init
```
<br>

``` $ cd ../
$ git clone -b master https://github.com/raspberrypi/pico-examples.git
```

![image](https://user-images.githubusercontent.com/114244849/194981933-96bd988f-adaa-441d-9b98-f83c752cbc15.png)

- Now run the following commands :
<br>

```
$ cd ./pico-examples/
$ mkdir build
$ cd build
$ export PICO_SDK_PATH=../../pico-sdk
```

- Now run the following command : `$ cmake ../`  which allows you to build examples and programs.

![image](https://user-images.githubusercontent.com/114244849/194982511-fc7a6dbf-36ce-4655-b0fd-1897309d6487.png)


# Guide to the Hello World Example for RP2040

- Firstly, we navigate to the `build` directory in the `pico-examples` folder using the following commands:

<br>

```$ cd ./pico/pico-examples/build
   $ cd ./hello_world
   $ make -j4
   ```
   
   ![image](https://user-images.githubusercontent.com/114244849/194985554-4a8e6427-d0de-46d0-8085-299b1e069b26.png)

-This step will generate build files.  The file `hello_usb.uf2` needs to be placed in the RP2040, for it to be run. To do this, firstly we will hold down the BOOTSEL button, once the board is plugged in to the host computer. Now, press and release the RST button, which makes the RP2040 show up as a USB.
Then drag and drop the `hello_usb.uf2` binary into the RP2040 . Once, this is done the RP2040, will reboot and the code will start executing.

- We will access the serial console to view the output. Navigate to your device manager to find out which `COM` port your board is connected to. 


   

