##Introduction

Klipper is an open source custom firmware for 3d printers that allows for advanced printer control and customizations.
Klipper provides a unique and powerful set of capabilities on top of the existing firmware. Klipper's advanced features
include:

- G-code macros: Klipper can execute G-code macros, used for simplifying complex or repetitive tasks, and to create
  custom G-code programs for specific tasks.
- Variable layer heights: Klipper can dynamically adjust layer heights, allowing for better quality prints.
- Customizable printer settings: Klipper allows for customizing various printer settings, such as maximum acceleration,
  jerk, and Z-axis height.
- Enhanced bed leveling: Klipper's bed leveling routines are more sophisticated than the ones typically found in
  firmware, allowing for better print quality.

**Note:** Klipper is not compatible with all printer touch screens (eg. Neptune 3), so prints will have to be monitored through the web interface exclusively.


##Installation

There are multiple ways to install and setup Klipper. For this tutorial, a tool
called [Kiauh](https://github.com/th33xitus/kiauh) is used. It is also assumed that a raspberry pi is used.

###Requirements

- A Raspberry Pi or other linux machine that is connected to the printer via USB

###Step 1 - Cloning the installation tool
SSH into your raspberry pi and clone [Kiauh](https://github.com/th33xitus/kiauh) with the following commands.

`cd ~`

`git clone https://github.com/th33xitus/kiauh.git`

Run it with
`./kiauh/kiauh.sh`

###Step 2 - Software installation

Follow the instructions on the interface to install the following in this order:

1. Klipper

2. Moonraker

3. Mainsail or Fluidd (Both are good choices, but Fluidd will be used for the rest of the tutorial )

###Step 3 - Building the firmware

Back out into the main menu, and then navigate to "Advanced".

Choose the option "Build only" and follow the instructions for your printer if applicable, or find the architecture information online

<details markdown="1">
  <summary>Elegoo Neptune 3</summary> 

  Config by [JerryNGM](https://github.com/jerryngm/)

- Micro-controller Architecture (STMicroelectronics STM32)
- Processor model (STM32F401)
- Bootloader offset (32KiB bootloader)
- Communication interface (Serial (on USART1 PA10/PA9))
</details>

###Step 4 - Firmware installation

The tool will output a firmware file. Install this firmware accordingly with your printers instructions.
<details markdown="1">
  <summary>Elegoo Neptune 3</summary> 
  
  Note. This firmware currently does not utilize the Neptune 3's LCD screen, it will not work while this is installed.

  1. Rename the file to `ZNP_ROBIN_NANO`

  2. Move the file to an empty SD Card formatted as FAT32 4096

  3. Turn off the printer

  4. Insert the SD Card and boot the printer


 
</details>

###Step 5 - Configuration

You should now be able to access Fluidd in a browser at the following address `fluiddpi.local`. 

Now you need to setup the `printer.cfg`. 

Open the "Configuration" tab on the left side and edit the config file. A preconfigured config file can be found online for most printers.

<details markdown="1">
  <summary>Elegoo Neptune 3</summary>

  [Config by BSAS](https://github.com/bsas/Neptune-Elegoo3-Klipper/blob/main/printer.cfg)
  
</details>

###Step 6 - Calibration

The printer must now be calibrated.

Detailed calibration and configuration can be found in the [klipper documentation](https://www.klipper3d.org/)

####[Calibrate probe offset](https://www.klipper3d.org/Bed_Level.html)

####[Calibrate PID](https://www.klipper3d.org/Config_checks.html#calibrate-pid-settings)

####[Calibrate rotation distance](https://www.klipper3d.org/Rotation_Distance.html#calibrating-rotation_distance-on-extruders)


###Printing
The setup should now be completed. You can now set up the printer as a physical printer in a slicer like SuperSlicer for wireless printing if desired.