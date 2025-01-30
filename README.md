# NI-Documentation-Examples
# Table of Contents
[About](#about)

[Use Cases](#use-cases---why-and-when-should-i-use-this)

* [LIST NI Systems](#list-ni-systems)
    - [PXI]{#pxi}
        - [PXI Hardware](#pxi-hardware)
        - [PXI Software](#pxi-software)
    - [Accessories](#accessories)



# About
The purpose of this repository is to provide use cases, documentation, and examples for using the LIST lab's NI Hardware. NI (National Instruments) is a manufacturer of industry-standard test and measurement hardware and software based in Austin, TX. You might know of them as "the LabVIEW company."

The lab's primary DAQ (data acqusition) equipment is a PXI-System. PXI is type of modular instrumentation platform that features, among other things, a chassis with slots for a controller capable of running a real-time operating system (RTOS) and peripheral modules that connect over a high speed PCI/PCIe bus. Peripheral modules can be anything from analog or digital I/O cards, function generators, FPGA boards, etc. Think of it as a really powerful computer with I/O and the capabilities of any typical boxed instrument you'd find on the shelf in an electronics lab. In short, it's an incredibly powerful piece of equipment that allows the user to perform sophisicated automated testing. 

Some more info on PXI:
 - https://en.wikipedia.org/wiki/PCI_eXtensions_for_Instrumentation
 - https://www.ni.com/en/shop/pxi.html

NI has various hardware offerings. PXI is the most powerful and also highest cost. The chassis was probably $20,000. Most of what we do in the lab *really* doesn't require the use of PXI. Large companies, like a Blue Origin would probably (they do!) use one of these if they needed to collect 300 strain gage meaurements at once. For our purposes, lower cost PC-based DAQs, such as the USB X-series DAQs or CompactDAQ, could probably suffice, BUT PXI does give you added flexibility and higher channel count. 

PXI also has some added complexities that can make it challenging for users who are unfamiliar with the NI platform. My goal with this document is to make it easier to get you started, make using the equipment easier, and to demonstrate how to use this tool to make your testing more efficient by adding automation. 

# Use Cases - Why and When Should I Use This?
Anytime you want to create a test or control system with some graphical user interface! You can automate and customize many features using this system's software and hardware to make your tests more efficient. Here are a few examples (the modules in parathesis are capable of the use case):

- Collect analog voltage or current data from sensors or a circuit over time, process, visualize, and log (PXIe-6361/PXI-6124/PXI-6255)
- Arbitrary function generator (PXI-5402,PXIe-6361/PXI-6124/PXI-6255)
- Automate a frequency sweep across a range of frequencies (PXI-5402/PXIe-6361/PXI-6124/PXI-6255)
- Run that frequency sweep AND collect analog voltage or current data over time (either any of PXIe-6361/PXI-6124/PXI-6255 or use the PXI-5402 for FGen and PXIe-6361 for input)
- Any kind of triggered analog or digital acquisition or control (PXIe-6361/PXI-6124/PXI-6255)
- Any kind of simultaneous analog or digital I/O (PXIe-6361/PXI-6124/PXI-6255)
- Adjustable power supply (PXI-4110)
- Non-deterministic control loops (from really low update rates, like once a minute or 1 kHz) (PXIe-6361/PXI-6124/PXI-6255)
- Deterministic control loops and repeatable nanosecond level precision timing (PXI-7854R)
- USB camera acquisition 
- USB or serial device control
- And much, much more...


# LIST NI Systems

Below is the list of NI hardware that the LIST lab currently owns. Currently, it is only the PXI, but if we get more, it will be added below.

## PXI

The software and drivers are installed on the lab Lenovo PC, but you can also install on your personal Windows machines. Linux will run LabVIEW, but you'll want to check driver compatibility.

### PXI Hardware
#### Chassis
- PXIe-1082
    - 8-slot (4 Hybrid, 2 PXIe, 1 PXIe timing)
    - The modules detailed in the #modules section fit into this equipment
    - https://www.ni.com/docs/en-US/bundle/pxie-1082-specs/page/specs.html
#### Controller
- PXIe-8101
    - NOTE: this hardware does not support NI Linux RT and thus is recommended for upgrade
    - For list of software installed, see the #pxi-software section
    - 2.0 GHz, Single-Core Processor (Intel Celeron 575) running PharLap RTOS 
    - 'Brains' of system, Ethernet Ports, USB ports, integrated hard drive, DVI port
    - https://www.ni.com/en-us/support/model.pxie-8101.html?srsltid=AfmBOopLhgjzB5uA5tovUplBdNuWRRRt0CZY0_3eIk4rBw3mhH0lLpnc
#### Modules 
- PXIe-6361
    - *Use Case*: General data acquisition or signal generation
    - Multifunction Analog/Digital I/O, Counter, up to 16 channels, triggering capabilities, 16-bit
    - https://www.ni.com/docs/en-US/bundle/pcie-pxie-usb-6361-specs/page/specs.html
- PXIe-6124
    - *Use Case*: General data acquisition or signal generation BUT less channels and higher sample rates
    - Multifunction Analog/Digital I/O, 4 AI (16 bit), 2 AO, 24 DIO, simultaneous sampling
    - https://www.ni.com/docs/en-US/bundle/pxie-6124-specs/resource/372526b.pdf
- PXIe-4330
    - *Use Case*: Strain gages, load cells, any measurement require a bridge or Wheatstone bridge
    - Bridge Measurements, 8-channel, 24-bit, 25 kS/s, simultaneous sampling
    - https://www.ni.com/docs/en-US/bundle/pxie-4330-4331-specs/resource/375487c.pdf
- PXI-4110 (2x)
    - *Use Case*: Power Supply
    - Programmable, two isolated and single non-isolated channel, +/- 20 V, up to 1 A
    - Currently DCPOWER0 but can be renamed. Note, you must refer to this module by its name shown in NI MAX
    - https://www.ni.com/docs/en-US/bundle/pxi-4110-specs/page/specs.html
- PXI-6255
    - *Use Case*: General data acquisition or signal generation, but more channels (40 diff, 80 SE)
    - NOTE: the 62xx series has been replaced by the 63xx series. Only use this module if you need the higher channel count
    - Multifunction, M-series, 40 diff channels, 16-bit, 1.25 MS/s
    - https://www.ni.com/docs/en-US/bundle/pci-pxi-usb-6255-specs/page/specs.html?srsltid=AfmBOoq-5YzM1bHs9xQWJFWIWizD94z_7dbEns4KCNUG1NWEAg1sSLXY
- PXIe-4322
    - *Use Case*: Analog output, signal generator
    - 16-bit, 8 channel, 250 kS/s Ch-Ch Isolated Analog Output
    - https://www.ni.com/en-us/shop/model/pxie-4322.html?srsltid=AfmBOop9KFZ59ro0JnUZ9uBikUgKl5nYz7Hw6ZH0Jz0bL3-PylhL3WtJ
- PXI-5402
    - *Use Case*: Arbitrary function generation
    - 20 MHz, 1-channel, 14-bit waveform generator
    - Working! Named FGEN0 and needs to be manually typed in FGEN resource control -- can rename in max
    - https://www.ni.com/en-us/support/model.pxi-5402.html?srsltid=AfmBOor-52pWNQ0vhzAySwSrVR14bcsujI4jwzUNhLZO8XeI6y1pwioE
- PXI-7854R
    - *Use Case*: SUPER fast and repeatable timing, control loops. Like, if nano-second level precision is required. 
    - R Series Reconfigurable I/O (AI, AO, DIO), 8 AI, 8 AO, 96 DIO lines, 750 kS/s AI rate
    - Need compactrio versions 15.0 and later and R series Support installed on host
    - works with NI-RIO 21.9 with COmpactRIO support 21.0, R Series Multifunction RIO support 21.3!
    - https://www.ni.com/docs/en-US/bundle/ni-78xx-api-ref/page/target2devicehelp/pxi-7854r.html?srsltid=AfmBOoodERm-_UESRxWNusYNZirWRwS4A6CTXwSX_uOjFzTJ2HkIT5Kv


### PXI Software
Best case is to use LabVIEW, but you can also use C, .NET, Python. This document provides examples in LabVIEW. Information on LabVIEW: https://www.ni.com/en/shop/labview.html

Here is a list of software current installed on the PXI controller:

### Accessories

## Notes
- Remote PXI devices will not be seen in Instrument Studio
- https://www.ni.com/en/support/documentation/bugs/21/ni-dcpower-21-0-known-issues.html for dcpower 
- working for eric's PC and the lab Lenovo

