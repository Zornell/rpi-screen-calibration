# rpi-screen-calibration
Configuration to set orientation of a raspberry pi touchscreen 

The scripts in this repository allow easy configuration of the display 
orientation and the touchscreen calibration. 

I wrote this to rotate the display output of my raspad, but this should work
for any touchscreen.

## Requirements


```
apt install ansible
```

I am using ansible because i did not want to care about any errors that might 
occur. It is rather slow but a bash script which does the same thing shouldn't
be too complicated.

## Details

The script will change rotation in the `/boot/config.txt` file and add a
xorg touchscreen calibration config to folder `/usr/share/X11/xorg.conf.d`.

Make sure the `MatchProduct` identifier in all the xorg configuration files
matches your touchscreen. You can list all input devices with
`xinput list`.

The rotate script is a wrapper for the ansible playbook. It takes one argument
which is the number of 90 degree turns the display will be rotatet (counter-clockwise).

## Further reading

Using xinput_calibrator did not work for me. I guess they changed how input 
calibration works.

* https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=78805
* https://wiki.archlinux.org/index.php/Talk:Calibrating_Touchscreen
* https://wiki.ubuntu.com/X/InputCoordinateTransformation
