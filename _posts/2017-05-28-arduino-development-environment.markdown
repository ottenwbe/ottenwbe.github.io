---
layout: single
title: Arduino Development Environment
categories: arduino
comments: true
---

I recently bought an Arduino Starter Kit.
On the cardboard box it says _'Have Fun'_. Guess what, I do have fun with my Arduino! To maximize the fun for others I write this tutorial. I describe the small hurdles I still had to get over when setting up an Ardunio development environment on my Linux system.

## Arduino: What is that?

Arduino is an open-source computing platform and consists of hardware
and software.
Hardware-wise a family of circuit boards with microcontrollers offer hobbyists the opportunity to easily implement and prototype electronic projects.
The programs hobbyists can write in C or C++ control the circuits via analog or digital I/O pins.
The official website provides an [Integrated Development Environment (IDE)](https://www.arduino.cc/en/Main/Software) that can be used for developing and uploading said progams.

Arduino projects can easily interact with their environment through sensors and actors.
For instance, temperature sensors and DC motors, just to name a few.
To this end, the Arduino plattform is a solid foundation for Internet of Things (IoT) projects.
            
## Getting Started on Linux

The booklet in the Starter Kit and the official [website](https://www.arduino.cc/en/Guide/HomePage) are incredibly helpful in getting started.
However, at least I overlooked the following [configuration details](http://www.arduino.org/learning/getting-started/arduino-ide-on-linux-based-os). 


### Installing the IDE

On a Fedora system, there are two options to install the IDE:
i) using Fedora's package repository or ii) dowloading the binary from the Arduino web-site. I recommend the latter option, but I describe both.

At the time of writing this blog, the version that can be installed from the repository is  ```1.6.4```. The IDE is then simply installed as follows:

    sudo dnf install arduino 
            
However, the Arduino web-site already provides a newer version ```1.8.2```, which offers some nice additional features (e.g., Export Compiled Binary). Hence, I recommend this version.

    wget https://www.arduino.cc/download.php?f=/arduino-1.8.2-linux64.tar.xz -O arduino.tar.xz
    tar xvf arduino.tar.xz
    sudo mv arduino-1.8.2/ /opt
    cd /opt/arduino-1.8.2
    ./install.sh

### Configuration

There were several smaller configuration issues I had to fix before getting started:

1. On my Lenovo Yoga 900 with a Quad HD display I had to tweak the UI since otherwise the text was too small to be read.
Thankfully, the IDE in version 1.8.2 offers an option to scale the interface (File->Preferences->Scale Interface).
                          
1. The second problem I faced occurred when I tried to upload my first program to the Arduino board. I got the following error message:
         
   ```
   can't open device "/dev/ttyACM0": Permission denied 
   ```

   The solution was rather simple, I added myself to the dialout group.
   
    ```
    sudo usermod -a -G dialout <user>
    ```    
  
## Tools
  
To help me get started I installed two other tools. 
First, for documentation purposes I installed [fritzing](http://fritzing.org/home/).
Second, for testing my projects locally on my Laptop I installed [Simuino](http://web.simuino.com/). 
  
### Fritzing for designing

The tool can be installed with the Fedora package manager. Other [distros](https://launchpad.net/ubuntu/+source/fritzing) also seem to offer fritzing.

        sudo dnf install fritzing
        # Start the fritzing tool
        Fritzing

Frizing has multiple views which are very helpful for documenting projects.
For instance, the ```breadboard view``` allows any novice, like myself, to easily draw the circuit design due to the visual representation of the Uno, the breadboard, and other components.

![Breadboard View]({{ site.url }}/assets/images/2017-05-28/thermometer_bb.png)

A formal ```schematic view``` is automatically generated from the breadboard view.
  
### Simuino for simulating the Arduino
     
To install the tool, follow the [get started guide](http://web.simuino.com/get-started).

After you compiled the program you can start to simulate your C or C++ code.
Copy your *ino file to the sketchbook folder of simuino.

    cp *ino <path_to_simuino>/sketchbook

Then start the tool.

    ./simuino

After the ncurses UI is up you can list and load your project:

    list
    # select the *.ino file, e.g., #5
    5
    # load the program
    load
    # finally run the program
    run


# Conclusion

Building small IoT projects, e.g., for home automation, is easy and fun with Arduino.


                
     