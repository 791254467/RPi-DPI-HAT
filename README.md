# RPi-DPI-HAT
Raspberry Pi HAT (Hardware Attached on Top) for TFT-Displays with DPI (Display Parallel Interface).


[![RPi-DPI-HAT](https://github.com/watterott/RPi-DPI-HAT/raw/master/hardware/RPi-DPI-HAT_v10.jpg)](http://www.watterott.com/en/RPi-DPI-HAT)


## Shop
* [RPi-DPI-HAT](http://www.watterott.com/en/RPi-DPI-HAT)
* [40-Pin FFC-Extenter](http://www.watterott.com/en/40-Pin-FFC-extenter)
* [Bundle: RPi-DPI-HAT + 5" 800x480 Display without Touchpanel](http://www.watterott.com/en/5-800x480-RPi-DPI-HAT)
* Compatible TFT-Displays (Touchpanel cannot be used):
  * [5" 800x480 Display without Touchpanel](http://www.watterott.com/en/5-800x480-TFT-Display-without-TP)
  * [5" 800x480 Display with resitive Touchpanel](http://www.watterott.com/en/5-800x480-TFT-Display)
  * [7" 800x480 Display with resitive Touchpanel](http://www.watterott.com/en/7-800x480-TFT-Display)


## Features
* 40pin connector for TFT-Display
* LED Backlight Boost Regulator (up to 35V)
* Single 5V Power Supply via GPIO connector
* Note: The HDMI and video output cannot be used at the same time with a DPI display.


## Hardware
* [Schematics + Layout](https://github.com/watterott/RPi-DPI-HAT/tree/master/hardware)


## Software
* Install device tree blob ([originally from Robert Ely](https://github.com/robertely/dpi666)):
    ```
    $ sudo apt-get install device-tree-compiler
    $ wget -N https://raw.github.com/watterott/RPi-DPI-HAT/master/docu/dt-blob-dpi.dts
    $ sudo dtc -I dts -O dtb -o /boot/dt-blob.bin dt-blob-dpi.dts
    ```

* Open the file ```/boot/config.txt``` and add the following lines at the file end:
    ```
    $ sudo nano /boot/config.txt
    ```
    ```
    # disable SPI and I2C
    dtparam=spi=off
    dtparam=i2c_arm=off
    
    # enable 800x480 display (TFT050-3, TFT070-4)
    enable_dpi_lcd=1
    display_default_lcd=1
    dpi_group=2
    dpi_mode=87
    dpi_output_format=454661
    hdmi_cvt=800 480 60 6 0 0 0
    ```

* Reboot the system:
    ```
    $ sudo reboot
    ```
