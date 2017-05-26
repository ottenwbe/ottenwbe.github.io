---
layout: single
title: Arduino Development Environment
categories: arduino, IoT
comments: true
---

I recently bought an Arduino Starter Kit. 
On the cardboard box it says _'Have Fun'_. Guess what, I do have fun with my Arduino!
To maximize the fun for others I describe in this tutorial the small hurdles I still had to get over when setting up 
my development environment on my Linux system. 

## Arduino: What is that?

Arduino is an open-source computing platform. It consists of hardware and software. 
This means a microcontroller/circuit board 
and an IDE for developing and uploading code that runs on the microcontroller.

Arduino boards can easily interact with their environment with sensors and actors.
To this end, the Arduino plattform is predestined as the backbone for Internet of Things (IoT).
            
## Getting Started on Linux

The booklet in the Starter Kit and the official [website](https://www.arduino.cc/en/Guide/HomePage) are incredibly helpful in getting started.



http://www.arduino.org/learning/getting-started/arduino-ide-on-linux-based-os

    * Very good descriptoin on website (see URL)
    * But some hurdles on Linux
    
    * Installation
        
        * Fedora was simple
            ```sh
            sudo dnf install arduino 
            ```
        * Otherwise, follow the instructions to install the IDE
        
        * Configuration: 
            * On my Lenovo with Quad HD I had to update the Graphics                         
         
        * Problem: 
            *   Permission Denied when uploading code
        
                ```
                can't open device "/dev/ttyACM0": Permission denied 
                ```
        
            * Solution: 
            
                ```
                sudo usermod -a -G dialout <user>
                ```
  
  ## Tools
  
  ### Fritzing for designing
  
  ### Simuino for simulating steps
     
     
                
     