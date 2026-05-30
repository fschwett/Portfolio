# Portfolio
### About me
My name is Fiete Schwettmann and this repository contains a small selection of private software, embedded and electronics projects I worked on over the last few years.

Over time I primarily settled on:

* Node.js for web applications
* .NET/C# for desktop applications
* C++ for AVR and ESP microcontrollers

I mainly work with:

* KiCad
* VSCode
* Visual Studio 2022
* FreeCAD / Fusion360

**Note:** These projects are being transferred from my private GitHub account to this one. As a result, the repository dates and contribution history may not reflect the original development timeline.

## Projects included

* #### [Doorbell sniffer](https://github.com/fschwett/Portfolio#doorbell-sniffer) - a minimally invasive RF transmitter for doorbells

* #### [Morse code trainer](https://github.com/fschwett/Portfolio#morse-code-trainer) - a simple website for Morse code training

* #### [RC servo PWM to digital](https://github.com/fschwett/Portfolio#rc-servo-pwm-to-digital) - a device that translates PWM to digital signals for simple remote controls
  
* #### [Resistor array](https://github.com/fschwett/Portfolio#resistor-array) - a classic resistor array for prototyping

## Doorbell sniffer

### Repo:

[github.com/fschwett/doorbell-sniffer](https://github.com/fschwett/doorbell-sniffer)

### Idea:

I can't hear my doorbell everywhere in my house and I wanted to change that without changing too much of the electrical installation. Also I didn't want to use any external power and instead only use the doorbell's power, hence the term "sniffer".

### Concept:

Doorbells in Germany usually operate using SELV (safety extra low voltage) which I take advantage of. This reduces the need for a big and complicated power supply. In my specific case the transformer is rated 8 VAC. Due to soft regulation characteristics the actual output is 16 VAC if not connected to a load. Using a full bridge rectifier I charge a capacitor bank which then powers a small RF transmitter. The receiver side can just be connected to anything. In my case a small MCU making a buzzer beep.

### Implementation:

I built the device on perfboard. The rectifier is made of Schottky diodes and I am using a 3000 µF capacitor bank along with some filter caps. To prevent overcurrent, the bank is charged through a resistor. The RF module I ended up using is an ASK transmitter (TX118S) that can directly handle the rectified voltage, making an additional voltage regulator unnecessary. Full calculations and in depth design choices are documented in the corresponding [repo](https://github.com/fschwett/doorbell-sniffer).

## Morse code trainer

### Repo:

[github.com/fschwett/morse-trainer](https://github.com/fschwett/morse-trainer)

### Idea:

I wanted a simple website for practicing Morse code with the Koch method on the go. Other websites lacked some of the customization options I wanted, so I built my own.

### Concept:

The Koch method is a widely used method for learning Morse code. When practicing, five characters are played in Morse code and you try to immediately write them down. This makes it closer to learning a language rather than decoding a code, allowing you to become fluent much more quickly. Additionally, not all characters are practiced from the beginning. Instead, you start with only two or three characters and gradually build your way up.

I wanted to have a website that gives me full control over which characters, speeds, and other settings I wanted to practice with. I ended up implementing three different modes for different types of training, each with a number of settings to optimize the learning experience.

### Implementation:

I chose to use a simple HTML/CSS/JS website. I used Bootstrap because I actually wanted to practice Morse code rather than spend endless amounts of time designing fancy GUIs. To play the sounds, I use the Web Audio API.

For a few months, the website ran on an Apache server, until I didn't need it anymore. I wanted to keep it as simple as possible and have a way to access it from any device, so I completely avoided anything that required a complex backend system. I wanted it to run on any device capable of rendering HTML and on any server capable of serving static files. This way, I would not have to worry about migrations—I could simply copy the files to any server at any time and everything would continue to work.

## RC servo PWM to digital

### Repo:

[github.com/fschwett/](https://github.com/fschwett/)

### Idea:

Most simple remote control systems can only output PWM signals for servo control but no digital output. Most remotes have toggle switches to set predefined servo positions. This device converts said signal into a digital output.

## Resistor array

### Repo:

[github.com/fschwett/resistor-array](https://github.com/fschwett/resistor-array)

### Idea:

I wanted to have a resistor array for test purposes. After seeing extremely expensive ones online I decided to create my own. My plan was to order it along with other PCBs, but that didn't end up happening.

### Concept:

An array of resistors which can be added to or removed from the total resistance. I wanted to order five PCBs to be able to play around with values more freely and be able to for example coordinate two resistances. I went with the classic 1, 2, 3, 4 design most of these arrays use giving me a range of up to 11.111.110 Ω.

### Implementation:

Even though it was never ordered, this PCB was designed for the slide switches and resistors I had laying around. I decided to go with SMD to eliminate the risk of shorting out or falsify the resistance by creating a shunt. 
