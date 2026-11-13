# New Build Guide
A simple step by step guide to configuring the raspberry pi for a CAN HAT.


## Assumptions
- You will be expected to know how to copy / "burn" an image to an sd card using either balena etcher or raspberry pi. The instructions to do that are not in the scope of this guide. Burn the default "base" image on the main readme. 
- You will be expected to know how to push files from your local device using SCP to the remote pi.


## Step By Step Instructions

- Burn the latest version of the SystemCore Base Image

- Put the card in your raspberry pi once its been burned

- Connect to the wireless network "SYSTEMCORE" using the password "PASSWORD" (upper case sensitive)
- OR connect through ethernet

- from the main dashboard (robot.local) click on the "terminal" app

- Create the mount point for the hidden partition
```
sudo mkdir -p /mnt/hardware_boot
```
- Mount the partition
```
sudo mount /dev/mmcblk0p2 /mnt/hardware_boot
```
- Edit the config.txt
    - Open the file using the following command
    ```
    sudo nano /mnt/hardware_boot/config.txt
    ```
    - Remove the full contents of the file 
    - Copy and paste the full contents to this config.txt file and save ( use the corresponding contents of  config_with_fd.txt or config_with_nofd.txt )
    - Save and close out of the file by using the following key Sequence 
    ```
    Ctrl + O
    Enter
    Ctrl + X
    ```
    - Unmount the partition and reboot the device
    ```
    sudo umount /mnt/hardware_boot
    sudo reboot
    ```
- Open the folder for your can header (fd, no-fd, no-fd-plus)
- Copy the contents from fd/systemcore-can-fd-setup or no-fd/systemcore-can-nofd-setup to the home directory of the pi from your local device using command line.
```
For FD:
scp -r systemcore-can-fd-setup systemcore@<pi-address>:/home/systemcore/

For NO FD:
scp -r systemcore-can-nofd-setup systemcore@<pi-address>:/home/systemcore/

```
- Execute the installer in the command by entering the folder directory
```
Use one of the below commands corresponding to your CAN Board
cd ~/systemcore-can-fd-setup 
or 
cd ~/systemcore-can-nofd-setup 

sudo bash ./install.sh
sudo reboot
```

- Install the canivore drivers by installing the .ipk as an app in the 4th tile option on the main dashboard.
    - Reconnect to the systemcore network if necessary
    - Select add packages in the web dashboard ( it is unclear which of the follow steps needs to be done first)
    - Drag and drop the first canivore-usb-kernel_1.18_aarch64.ipk file to install
    - Drag and drop the second canivore-usb_1.16_aarch64.ipk file to install
    - reboot

- Verify all is running fine as expected
```
From terminal execute the following command to validate the bus is good and all channels are as expected . We expect only the first 2 channels to be listed as physical and all others to be virtual.

ip -br link show | grep can_s

From the terminal execute the following command to validate that the can bringup service is online and active 

systemctl is-active can-bringup robot
```
- Update necessary firmware on the motor
    - CTRE
        - Open pheonix tuner preview application
        - Connect to the robot using dashboard or ip address
        - Update the firmeware to the latest 2027 version
    - REV
        - Connect to the robot using dashboard or ip address
        - Install the .ipk as an app on the main dashboard
        - Open REV Hardware Client 2
        - Install the 2027 SPARK MAX / SPARK Flex Firmware

- Deploy robot code
    - This project is forked from BobCat Robotics, they have included example projects for both the Commands v2 and V3 frameworks. You can find the projects in the project_examples folder of this repo. Select the version that corresponds to your hardware. Deploy as normal.

