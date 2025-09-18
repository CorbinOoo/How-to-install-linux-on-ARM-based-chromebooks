<p>Step 1. Flash the proper os onto a flash drive that you can plug into your Chromebook. I would recommend using Balena Etcher (https://etcher.balena.io/) for the os writing. You can get the proper os from here (https://github.com/hexdump0815/linux-mainline-on-arm-chromebooks).</p>
<p>Step 2. Once you have that done, you will need to enable developer mode on your Chromebook. You will need to press Esc + refresh (the rotating circle) + power at the same time to enter recovery mode (must be done while the computer is in Chrome OS). Your screen should look like this: <img src=https://github.com/user-attachments/assets/1bd0f4c5-adb6-4074-88f1-5c53dd4f4f08></p>
<p>Step 3. Press Ctrl + D. It will say that you will delete all data on your Chromebook (**<b>BE SURE TO BACKUP ALL OF YOUR FILES TO A CLOUD, DRIVE, OR STORAGE OF YOUR CHOICE. YOUR DATA IS NOT BACKED UP AUTOMATICALLY</b>**). Press the "Confirm" button.</p>
<p>Step 4. The next step is to enable booting from a USB. You will need to press the right arrow key (forward), the Ctrl key, and the Alt key at the same time. This will log you into the "VT-2" root shell. Once you are there, you will need to enter "chroot" as the username (there is no password). From here, type in "enable_dev_usb_boot". In the window, you may need to use "sudo" before the command if it doesn't work.</p>
<p>Step 5. The next step is to plug in the USB drive that you created in Balena Etcher during step one. You should shutdown your Chromebook fully with the USB drive plugged in. When it turns on, you should see the recovery screen. </p>
<p>Step 6. press Ctrl + U on the recovery screen (**NEVER PRESS SPACE, AS IT WILL RUIN THE PROCESS, AND YOU WILL NEED TO START OVER**). Now that you are booted into Linux, you will see a gray login screen with a box to the left that asks for a username (shown here). <img src=https://github.com/user-attachments/assets/87f9c238-8b69-4321-ac55-0901d6bb66c9>
The username is "linux" and the password is "changeme". For some reason, you cannot change the username from "linux" on the login. After that, you will open the terminal (shown here).<img src=![terminal photo](https://github.com/user-attachments/assets/1485fae0-36b1-4abe-ba96-ab62f5b8827a)</p>
<p>Step 7. The next steps can be a bit complex, but I will walk you through them as best as I can. In the terminal, type in "lsblk" and press enter. <img src=https://github.com/user-attachments/assets/a6bd01ed-f67f-4eb4-b947-adcd5ee25851></p>
<p>Step 8. look for the drive that says "sda". This is your flash drive. Next, look for the "mmcblk0" or "mmcblk1" text. This is the eMMC storage (if you have a different storage than eMMC, then this will look different). This will help determine the next terminal command.</p>
<p>Step 9. type "sudo wipefs -a /dev/*****enter either "mmcblk0" or "mmcblk1" depending on what lsblk said*****" example: "sudo wipefs -a /dev/mmcblk1" (**CAUTION, THIS WILL WIPE YOUR CHROME OS, WHICH IS NOT REVERSABLE**).</p>
<p>Step 10. enter "sudo dd if=/dev/sda of=/dev/****type in what is says in in lsblk
 <img src=![lsblk photo](https://github.com/user-attachments/assets/79da67f2-f963-4de5-a177-6023ce41655a)</b> (your specific mmcblk will be in the spot on the photo that is circled****) bs=4M status=progress conv=fsync". This will copy the contents of the flash drive that is plugged into your Chromebook to the actual Chromebook's eMMC drive. With this command, I would recommend pressing Ctrl + C after 7 gigs have been copied, as this will go on forever (im not 100% sure on this). Once the copying has completed, you can turn off the computer by pressing the top right button that says "linux", then press power off.</p>
<p>Step 11. Unplug the usb drive and turn on your computer, boot into linux with control + D ******DO NOT PRESS ENTER OR SPACE AS IT WILL BRICK YOUR CHROMEBOOK!!!******</p>

Congratulations! You have now completed your linux installation. Feel free to tweak the OS to your heart's desire.





