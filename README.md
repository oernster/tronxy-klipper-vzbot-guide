# tronxy-klipper-setup
How to setup klipper on a tronxy x5sa

# Hardware required
USB cable for pi/linux box/windows box to printer.

Raspberry pi or linux box or docker container on a windows box with linux inside and bridging enabled as far as networking is concerned.

Min 32GB SD card for your pi (I recommend either SanDisk or Samsung).

Ideally no bigger than 32GB SD card (since some printers can't handle bigger than 32GB when flashing; I just used the 8GB one that came with the printer) 
to flash klipper firmware to the printer.

# Steps for a pi...

Note you can also just use linux and install via kiauh instead if you prefer.

KIAUH location: https://github.com/th33xitus/kiauh (Klipper Install And Update Helper)

To get it, do 'sudo apt install git' on your pi.

Then do 'git clone https://github.com/th33xitus/kiauh.git' and follow the instructions in the previous link.

If not using kiauh...

Flash MainSail to a minimum 32GB SD card for your pi.  You can download Raspberry pi imager to do this: https://www.raspberrypi.com/software/

You will need to define ssh enabled in the imager and set your username e.g. pi and password for the pi (don't forget this).

You will need to define your SSID (wifi name) and password for that too.

Flash and wait.

Insert into pi and turn on pi.

# Install klipper firmware

Go to this repo's directory: klipper-firmware and download the update.cbd file.

Copy it to your 8GB SD card supplied with the printer into the root directory.

Turn off Tronxy.

Insert SD card.

Turn on Tronxy x5sa.

It should beep twice when the firmware has been flashed; there will be nothing on the screen.

# Klipper config / Mainsail setup on pi

Copy this repo's klipper_config/printer.cfg file to your pi either using putty or scp (secure copy) and put it into the directory /home/<username which might be pi>/klipper_config/

# Install Fing app on your laptop/PC.

Go to https://www.fing.com and download and install fing.

Make sure you're on the same network you configured for your pi on your PC / laptop.

Run Fing and check devices for your pi's IP address.

Go to that IP address in your favourite browser.

You should see Mainsail come up nicely.

# Klipper Screen

If you want a touch screen as well as a browser interface for your printer/pi, then you'll need to install kiauh as described above.

Then in the kiauh menus install klipper screen and then reboot the pi.

# Troubleshooting...

If, for some reason, your mainsail reports an mcu error then it's likely your pi's printer.cfg file in the mcu section has an invalid USB id.

To fix this ssh into the pi (ssh <username>@<IP address from fing> and enter your password)

Now enter: 'ls /dev/serial/by-id' (make sure no cameras or other USB devices are connected first, only the printer.  Then copy the text you see into the mcu section in printer.cfg, matching the existing format in the printer.cfg file I've provided. 
