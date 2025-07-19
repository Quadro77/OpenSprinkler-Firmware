# New Installation of the Unified firmware on a Raspberry Pi #
NOTE: your RPi must be running Bookworm (or at least Bullseye) in order to compile the latest firmware. If you are on older Raspbian (e.g. Buster), you need to ugprade your Raspbian first.



Open an SSH connection to the Raspberry Pi (or use a keyboard and monitor connected to Raspberry Pi)

### Run the following command: ###
sudo apt-get install git
cd ~
git clone --recurse-submodules https://github.com/Quadro77/OpenSprinkler-Firmware.git

*Below is the original, The one above is forked.

git clone --recurse-submodules https://github.com/OpenSprinkler/OpenSprinkler-Firmware.git*

 **### Change the directory to the firmware folder: ###**
cd OpenSprinkler-Firmware

### Build OpenSprinkler: ###
sudo ./build.sh ospi
Answer **yes** to the startup script.

This will generate an executable program called OpenSprinkler in the firmware folder, and also set up startup script for auto-run at startup.

NOTE: it has come to our attention that some Raspbian systems installed by NOOBs will take over GPIO 4 for 1-wire interface, but that OSPi needs GPIO 4 to send control signals to the solenoid valves. If you found that the firmware runs correctly but OSPi does not turn on valves correctly, one solution is to sudo open /etc/modules, and comment out the line containing w1-gpio, then reboot. Another solution is to reinstall Raspbian OS from scratch without using NOOBs.

The web interface should now be accessible from: **http://localhost:8080**. The default password to log into the web interface is **opendoor**.
