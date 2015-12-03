# rpi-shutdown
A python script to shutdown the Raspberry Pi.
Adapted from:
http://www.element14.com/community/docs/DOC-78055/l/adding-a-shutdown-button-to-the-raspberry-pi-b#

Created and tested for use on the Raspberry Pi 2 model B.

##What it is for.
Runs a script in the background to shutdown the Pi when a button is pressed.

##What it is doing.
References the GPIO pins in GPIO mode, GPIO18, instead of pin order, pin 12.
Uses the internal pullups, so a resistor isn't needed.
Runs "sudo shutdown -h now" to safely shutdown the Pi.

##How to use
Clone script to Pi.
Attach leads and a switch across pins 5(GPIO3) and a ground (pin 6,9,14,20,25,30,34 or 39).
Manually run script so we can verify it works. "sudo python shutdown.py"
Enable script to run at boot, such as cron.
Edit crontab "sudo crontab -e".
Add "@reboot python /home/pi/rpi-shutdown/shutdown.py &"
Push button and the Pi should shutdown.
Reboot and push button again to verify cron loaded the script.

##Note
The original script used GPIO18. I altered it to use GPIO3, since jumping GPIO3 to ground will also power on the Pi. So a single switch can now function as a on/off switch. Time will tell if this has long term issues. I haven't seen any other articles using GPIO3 to power off with.
