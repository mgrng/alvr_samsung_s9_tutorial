Tutorial on how to set up ALVR+SteamVR for an Samsung Galaxy S9+, including GearVR controller. Other phones might also work.

If you only want to watch videos or do things without a GearVR controller, consider https://github.com/alvr-org/PhoneVR?tab=readme-ov-file#installation as the setup is much more simple. You may still need to install/update Gear VR Services.

Please take care when looking for .apk files online, and upload them through https://www.virustotal.com/gui/home/upload if you are unsure. VirusTotal can sometimes come up with false positives, so Google the detections to see what type of detection they are before proceeding.

Last updated 2024-11-23.

# Requirements
- Samsung Galaxy S9+ (other Gear VR compatible phones will likely work)
- A headset to mount your phone (Ideally Gear VR, but you will not need to plug it in)
- Steam (ALVR uses SteamVR)
- Good upload speed (50mbps+?)
- Gear VR Controller (optional)

# 1. Gear VR Services
Every Samsung Galaxy S9+ device comes preinstalled with Gear VR Services.

On your phone, go to Settings > Apps > Search "Gear". If you don't have anything listed, you will need to install Gear VR Services.

iVRy provides a nice way of installing these apps. Plug your phone in, and install the following:
https://store.steampowered.com/app/992490/iVRy_Driver_for_SteamVR/ + DLC https://store.steampowered.com/app/1487090/iVRy_for_SteamVR_GearVROculus_App_Installer/

Plug in your phone, enable Developer mode, scroll down to USB debugging area and uncheck Verify apps over USB just in case.

With your phone plugged in, when launching iVRy Driver for SteamVR, select "Launch Install Gear VR System Files".

Follow the instructions, and then launch iVRy Driver for SteamVR again, this time selecting "Launch Install GearVR/Oculus Mobile App".

If the above doesn't work, try manually installing these apks. You may need to use adb (https://dl.google.com/android/repository/platform-tools-latest-windows.zip). Place apk in same folder as adb and run "adb install whateveryourapkisnamed.apk".

~~https://drive.google.com/file/d/1JBTyAi1i3Fj5Ol5bkMyAd2IGTA2UGgtZ/view Gear VR Services~~

*If you've messed up along the way with adb and ran commands like `adb uninstall -k --user 0 com.samsung.android.hmt.vrsvc` while trying things, you can reinstall the package if you have the package name by running `"adb shell cmd package install-existing <package name>"`

Once you have Gear VR Service, you can find it under Settings > Apps > Search "Gear VR Service". Click on it to open the app's settings, and Open the actual app.

On the top-right of the app, click on More, tap a few times on VR Service Version to enable dev options, and enable Developer mode, Add icon to app list, and Allow VR API without OSIG. Close the app for now, but you may have to reenter this app in the future to enable these options again if they turn themselves off (likely after you close Gear VR). 

To actually close Gear VR, you need to swipe down on the persistent notification, and click on Turn off.

# 2. Downgrading Oculus
After you have confirmed that you have Gear VR Service, the Oculus version installed by iVRy will crash on launch. To resolve this, you will need Oculus version 3.27.0.6.963. apkmirror or other archived versions will work. Uninstall Oculus, and install the older apk. You may need adb to do install this. This will also help you pair your GearVR controller.

# 3. Pairing Gear VR Controller (optional)
The GearVR controller isn't great for gaming, but works well enough as a simple laser pointer. 

https://www.samsung.com/hk_en/support/mobile-devices/connect-samsung-gear-vr-controller-via-bluetooth/

2 AAA batteries are required to power the controller. Hold down the Home button until the light flashes red, green, blue. Turn on your phone's bluetooth, and select the controller. Gear VR Services along with the downgraded Oculus are required. Once you tap on the controller in your Bluetooth , you are brought to the Oculus app where the controller pairs, and you are able to view the battery %, Device ID, and version. The callibration takes about 10 figure 8s to complete. If it takes you any longer, the controller might not be functional.

# 4. Setting up ALVR
The up-to-date version of ALVR by alvr-org seems to no longer support GearVR. The version I used is the final version of https://github.com/polygraphene/ALVR, v2.4.0-alpha5.

Download ALVR-setup-2.4.0-alpha5.exe from https://github.com/polygraphene/ALVR/releases/tag/v2.4.0-alpha5. This is the Desktop app. Follow installation instructions.

Download ALVRClient-GithubNormalOvr-release-v2.4.0-alpha5.apk. This is the mobile app. adb installation method may be required.

Follow ALVR instructions to pair your phone with your Desktop app. This can be done over the same wifi network. At this point, once you have connected your phone, SteamVR should be launching.

**At this point, if you attempt to launch the ALVR phone app and it redirects you to default Gear VR setup, you can troubleshoot in a few ways:
- Ensure you downgraded Oculus
- Ensure Gear VR Service has been set to Developer mode, and Allow VR API without OSIG
- Try manually adding an OSIG (This is a complicated process, I will explain it at the end under "6. OSIG")

Install the ALVR driver for your PC, found under the About tab. Mute the sound under the Sound tab unless you want your phone speakers repeating sounds. Enable your controller under the Controller tab, and reconfigure any buttons. I recommend setting your Reccenter button to the "Back" button on the Gear VR controller.

A very good internet connection (upload speed) is required to have a stable connection over wifi. Under the Video tab, adjust settings as high as you can without having a choppy image in the ALVR app.

# 5. Tips, Tricks, and Finalizing
Once you have confirmed your phone is connected with ALVR and streaming SteamVR, there are a few steps remaining.

Making sure not to plug in your phone to the USB-C socket on the Gear VR, mount your phone on your headset, with the screen facing the lens. See https://phandroid.com/wp-content/uploads/2014/12/gear-vr-droid-turbo-640x366.jpg or Google "How to use Samsung Gear VR with unsupported smartphones". You will want to have both mount pieces flipped up until they are diagonal, and push the top of your phone into the non-USB-C side. Then, push down towards the lens until your phone lies flat. The bottom of the USB-C side should support your phone (Samsung Galaxy S9+), while still being diagonal, exposing the USB-C. Pushing the non-USB-C mount bracket outwards will release the phone.

After your phone is mounted, with ALVR running on your Desktop, SteamVR will also be running on the bottom-right of your main monitor. Click on the top-left hamburger icon, and click on Room Setup. You should calibrate your headset as if it were a normal VR headset, to have a normal seated/standing height.

From the SteamVR menu, you can also Recenter your view. Aim your headset where you want to be facing while using it, and hit Recenter.

Put on your headset and calibrate the lens with the focus adjustment wheel.

From here, you can browse the SteamVR menus to download new apps, games, or whatever you have set up. Steam has a barebones VR media player you can access in the same hamburger menu for calibration.

If it is your first time in VR, I highly recommend only keeping the headset on for a few minutes at a time, as it is very easy to develop symptoms like dizziness and nausea. 
Stay away from anything too intense and ease yourself into it.

# 6. Adding an OSIG to your APK & Alternatives
I'm unsure if this step is necessary, but if you are encounting any issues with ALVR launching on your phone, you can try this.

Install adb, and use `adb devices` to find your device ID.

Visit https://developer.oculus.com/manage/tools/osig-generator/ , and register an account in order to access the Oculus Signature File (osig) Generator.

Enter your device ID, and download the file. Send this file to your phone.

Use an APK editor (I used apkeditor_1.9.0 from apkshub) to unpack and decode all files from your ALVR apk, and navigate to the "assets" folder.

Place your osig file in the assets folder, and build the apk. Install the new apk (may require `adb install <package_name>`).

If you absolutely cannot get ALVR to work, iVRy itself is a paid option I would consider. They have a free trial that turns monochromatic after 5 minutes to encourage you to buy the app. There are many alternatives out there, but I haven't done much research as ALVR works as a free option for me.


Hoping this helps at least 1 person somewhere struggling with a similar setup.


Credits to:
https://xdaforums.com/t/how-to-install-get-back-uninstalled-apps-apks-with-adb.3894235/
https://www.reddit.com/r/GearVR/comments/1etqgas/workaround_without_reset_oculus_has_stopped/
https://xrpotato.hatenablog.com/entry/2018/07/01/000000
