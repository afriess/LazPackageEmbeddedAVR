# LazPackageEmbeddedAVR
This is a project wizard as Lazarus IDE plugin for creating empty projects for Target embedded: AVR.
The device specific project settings are generated, a programmer command is optional for direct flashing of the device on key press from within the Lazarus IDE.
As special feature a device specific interrupt file is generated for easiest use of interrupts.

## Installation:
Download all files as zip. Unpack the zip to a random place. You will have to keep the files at that place after installation. Open the Lazarus IDE, and install the package. Therefore click menue "Package" -> "Open Package File (.lpk)".
Choose "lazpackageembeddedavr.lpk", the package dialog opens. Press "Use" -> "Install". Confirm to rebuild the Lazarus IDE.

LazPackageEmbeddedAVR doesn't do any compiler or programmer installation. You have to do it seperately. An easy way to install the proper FreePascal compiler is using FPCUpDeluxe. Also take care that your programmer software is installed properly and accessible by command line (usally it means it's added to the PATH environment variable, or using symlinks under Linux). 

## Usage:
After installation there will be a new item in the Lazarus dialog for new projects. The Item is called "AVR Embedded Project".


## Requirements:
FPC at least fixes 3.2 or trunk

Lazarus at least  2.0.0 or better - with OPM (Online PackageManager) installed. Laz_synapse from OPM

Arduino IDE at least 1.8.x for AVRDude and other specifix files (the zip version is ok, no installation required) if you want to work easy with Arduino

## Links
### English

Arduino <https://wiki.freepascal.org/Arduino>

Samples Lazarus-Embedded <https://github.com/sechshelme/Lazarus-Embedded>

GCC AVR Options <https://gcc.gnu.org/onlinedocs/gcc/AVR-Options.html>

### German
LazPackageEmbeddedAVR: Projekt-Dialog für Target AVR <https://www.lazarusforum.de/viewtopic.php?f=18&t=12054>

AVR embedded für verschiedene Controllertypen - geht! <https://www.lazarusforum.de/viewtopic.php?f=9&t=11718>

Re: Lazarus embedded mit fpcupdeluxe geht nicht <http://www.lazarusforum.de/viewtopic.php?f=15&t=11044&p=98353#p98353>

AVR Embedded Tutorial <https://wiki.freepascal.org/AVR_Embedded_Tutorial/de>

AVR Embedded Tutorial - Entry Lazarus and Arduino <https://wiki.freepascal.org/AVR_Embedded_Tutorial_-_Entry_Lazarus_and_Arduino/de>

# Documentation
## Devices add

### How to add controllers
(help from dlgNewAVRProject.pas)

If the FreePascal compiler supports controllers that are not yet listed in the dropdown menu then you can add the device yourself. 

Therefore copy the device specific file from your FreePascal installation to the subdirectory ''Devices'' of the package installation place. This is where you unpacked the package files before you started the package installation. The device specific file has the name of the device and the file extension .pp, e.g. ''atmega32.pp''. The files can be found in the fpc source directory under fpc/rtl/embedded/avr. Next time you start the new AVR project dialog, the controller will be listed automatically, no recompilation of the package needed.

The device specific source file ''uInterrupts.pas'' will be generated based on the device specific file.

To connect the correct instruction set to the device (optional), the file ''InstructionSetDefinitions.dat'' in the Subdirectory ''Devices'' has to be modified, just add a line with the end of the file with the device name and the instruction set seperated by a space character.


### How to add programmers
Programmers can be added easily.
    
For examples check the subfolder ''Programmer'' in the package installation directory. This is where you unpacked the files before you started the package installation.

For a new programmer add a line in the definition files ''AVRDude.dat'' or ''Others.dat''. The first string in quotation marks is the name of the programmer displayed in the pulldown menu. The second string in quotation marks is the command line for the programmer.


Next time you start the new AVR project dialog, your programmer will be listed automatically, no recompilation needed.

Also see the README.TXT in the ''Programmer'' subdirectory.
