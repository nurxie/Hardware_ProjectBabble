# Hardware/Firmware advance for [Project Babble](https://github.com/SummerSigh/ProjectBabble) of facial tracking

- This project is an addition to [**Project Babble**](https://github.com/SummerSigh/ProjectBabble). At this link you will find the project repository and the program for processing the image received from the video camera.

- This firmware is based on the already developed [**OpenIris**](https://github.com/lorow/OpenIris). project, some minor changes have been made to the program code to increase the quality of the picture.

- In this repository there will be only an addition in the form of *microcontroller firmware and instructions for assembling the* **mouth tracker** *itself*.


## How to run 
0. You will need an ESP32-CAM for assembly. It is better to purchase a board with a built-in programmer, but it can be connected separately. I advise you to use a standard OV2640 camera with a viewing angle of 60 degrees. ![Logo](https://synthiam.com/Uploads/Firmwares/HLT3KZKGG3F/HLT3KZKGG3F.jpeg)
1. Install Visual Studio Code. Download the [**latest Visual Studio Code**](https://code.visualstudio.com/download) and install it.
2. Install [**PlatformIO IDE**](https://platformio.org/platformio-ide) (_you can follow the link or install it from Visual Studio Code itself_)
- Once Visual Studio Code is installed, open it and install PlatformIO IDE for VSCode, an extension that will allow you to connect to the tracker, build and upload the firmware.  
3. Download this repository. 
- This can be done either by clicking on the green "**Code**" button --> "**Download ZIP**". 
- Or using command below (To use the command below, you need to have **git** installed on your computer. _Downloading via command guarantees complete download of all files_)
```bash
    git clone https://github.com/nurxie/Hardware_ProjectBabble.git
```
4. Open project
- Open the firmware in VSCode by going to PlatformIO, selecting open, then navigating to _Hardware_ProjectBabble_ folder and opening it.
- After opening the project, files for compilation will be additionally downloaded.
    ![Logo](https://i.imgur.com/c61Cpaz.gif) 
    (This gif was taken from the [**SlimeVR project website**](https://docs.slimevr.dev/firmware/setup-and-install.html) as an example.)

5. Configuring the firmware
- After successfully opening the project, you will see a list of project files on the left. You need to open the _**ini**_ folder and find the _**user_config.ini**_ file there.
    ![Logo](https://i.imgur.com/c61Cpaz) 
- Replace the placeholder (_YOUR_SSID/YOUR_PASSWORD_) text with your correct SSID (WiFi access point name), and password respectfully.
  - Special characters such as **!** and **@** are not supported. If you have a special character in your password or ssid, you will need to change it.
  - Spaces are not supported either. If you have a space in either, you will need to change it.
  - Make sure your wifi router has a 2.4 GHz band. While most do, this is not always the case. Setting each band (5GHz, and 2.4GHz) to different SSIDs is recommended, though not required.
  - Also, do not forget to select the channel of your Wi-Fi network. (default _**channel = 1**_)

6. Flashing a tracker
 - Connect ESP32-CAM via the programmer
   - First, connect your ESP32-Cam to your programmer. In the case of the ESP32-Cam-MB board, it's as simple as sticking it into the socket and then connecting it to your PC with a _micro-USB_/_mini-USB_/_USB type-c_ cable.

   - In some cases, there is a button labeled _IOO_ on the programmer. If that button exists make sure to hold it in while you plug the programmer into your PC, once plugged in you can release the button.

   - In the case of an FTDI programmer, the steps aren't as easy, so grab [**this guide**](https://randomnerdtutorials.com/program-upload-code-esp32-cam/) for how to set it up.
- Build your firmware
  - Press the build button at the bottom of Visual Studio Code. _This builds the firmware, but does not send it to the ESP yet._ ![Logo](https://i.imgur.com/EmSkhFp.png) (_at the bottom left of the program window is a blue or black button with a checkmark_)
- Upload your firmware
  - Сlick on the button that is located at the bottom left of the blue or black program with an arrow pointing to the right. ![Link](https://i.imgur.com/lI3PFVC.png)
  - The MB board does the reset for you. If you are using an FTDI programmer, follow the  [**instructions**](https://randomnerdtutorials.com/program-upload-code-esp32-cam/) mentioned earlier.

7. Checking the IP address and gaining access to the camera
- You need to connect via UART to the microcontroller and find out what IP address was assigned. To do this, you need any serial monitor, I recommend [**RealTerm**](https://sourceforge.net/projects/realterm/). You need to select the correct port and **115200 baud**.
- The output in the serial port will be similar to the example. You will see the IP address of your camera ![Logo](https://i.imgur.com/PoHP3NC.png)

8. Conclusion
- The allocated IP address should not change, but if this happens, you will need to check it again. You can, of course, allocate a separate IP address for the tracker, you can find information about this on the Internet.
- After that, you can put the IP address itself in the format _**http://192.168.0.206/**_ in the first field of the **Babble** program. Everything must work.
- If something doesn't work, you can to connect via SART to the microcontroller and read the error information. You can find solutions to problems on the [**OpenIris**](https://github.com/lorow/OpenIris) project page

# Super Conclusion
- Part of the photo, instructions and information was taken from the [**SlimeVR**](https://docs.slimevr.dev/) , [**OpenIris**](https://github.com/lorow/OpenIris) and [**EyeTrakingVR**](https://docs.eyetrackvr.dev/).
- This repository and the project itself are still under development, there may be changes.
- I advise you to use an external Wi-Fi antenna for the microcontroller to improve the stable video stream.

# TODO
- [x] Make a repository :tada:
- [ ] Adding 3d models for mounting the camera on the vr-helmet
- [ ] Adding 3d models of the camera body
- [ ] Adding Illumination (Infrared Illumination)

- [ ] Make a prefab for the unity vrchat model (sometime later ¯\_(ツ)_/¯ )