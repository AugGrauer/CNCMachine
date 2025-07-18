# CNCMachine
Open source repository for the CNC machine built by [Backyard Shed Engineering](https://www.youtube.com/@ShedStuffBuiltHere)

[![YouTube](https://img.shields.io/badge/YouTube-Backyard_Shed_Engineering-red?logo=youtube)](https://www.youtube.com/@ShedStuffBuiltHere)


This is a fully self-funded, opensource project done by two highschoolers. While we have tried our best to document everything, and make it as accessible as we can, there is still an aspect of DIY to this project. Before building, please study the CAD models provided. If you run into problems, open an issue and we will try to respond and improve this guide.

This machine is mostly 3D printed. 3D printer access is required. 
## License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Feel free to use this as a basis for your own project, or replicate it!

## Table of Contents
- [Specifications](#specifications)
- [License](#license)
- [BOM](#bom)
- [Use](#use)
- [Known Issues](#known-issues-)
- [Assembly](#assembly-)
- [CAD Models](#cad-models)
- [Wiring](#wiring)
- [Firmware/Software](#firmwaresoftware)
- [Putting it all together](#putting-it-all-together)
- [Media](#media)
- [Contributing](#contributing-)
- [Roadmap](#roadmap)
- [Changelog](#changelog)
  
## Specifications

  Build Area: 16x18x1 in 

  Total Footprint: 
  
  Supported Materials: Aluminium, wood, plastics. (Anything softer than aluminium)

  Motors: 3x NEMA 23, 1x NEMA 17 

  Spindle: Choice Spindle/Router/VFD. Designed for a Dewalt Trim Router. Easily Modified for a Makita 1 1/4HP Router

  Control Board: Arduino UNO w/ GRBL 1.1
  
  Power Requirements: 120V
  


## BOM
BOM is in the repository and also here:
https://docs.google.com/spreadsheets/d/1JcS2ukq2nQpIpGEV6_Kvxhg6B4QogmMNbcgQQ2et4MQ/edit?usp=sharing


# Use
  We have created this repository in order to make our CNC project as open source as possible. We were really proud to do this project for under $1000, and we want others to be able to as well. Feel free to use this as a basis to design your own, or to simply make your own version of our machine. We have included the BOM, all of our 3D models used, and our wiring diagram, as well as a few extra resources and our advice. We have further explanations on our youtube channel. ⏯️

## Known Issues 🐛
  This machine is by no means perfect, so there are a few problems we have encountered. Below is a list of the problems and if we have found solutions
  1. Electromagnet Interference: ✅
     - This is probably the largest issue encountered during construction and inital operation. After investigating, it turns out that our buildplate, and most metal on the body of the CNC machine is actually charged. We aren't sure why or from where, but we suspect that it is something to do with our stepper motors.
     ### **FIX**
       - To fix this, we used EMI shielding along most of the long wires which run from stepper motors to the electrical box. This is included in the BOM, and we had just enough to get most of our wires shielded. We found that there were a few specific areas which were worse, especially where the EMI shielding/ wires in general come in contact with the metal frame of the machine. We solved this by insulating those specific areas with electrical tape.
  2. Bed Leveling 🟠
     - We have been unable to really solve this. It isn't a terrible issue, and certainly doesn't prevent the operation of the machine. Take this into account when slicing models/preparing to cut stuff, as there may be a few corners (at least for us) which dont cut all the way to the buildplate. By using an overcut, you can compensate for this.
      ### **FIX**
       - We don't have a 100% fix, but if you plan to overcut by .1/.2mm, everything should cut through. If you don't want to do that, it is pretty easy to break the last little layer off and get a clean part.
  3. Alarms ✅
     - This machine alarms a decent amount. Don't be too alarmed (See what I did there). If you are using UGS/GRBL like we did, you can reset and unlock the machine to continue. Usually alarms occur due to a voltage change, or a serious problem. After frequent use and learning, we found that most of our alarms occur when turning on the router. This is pretty easy to work with, as we just reset and continue. If your machine is constantly alarming, test it for voltage differences/charges in weird places. Try insulating. The limit switches are USUALLY not actually the problem.
      ### **FIX**
       - Reset and unlock machine. If that doesn't work, test and insulate/ground different areas. Limit switches are pretty reliable for us, so that was almost never the issue.
  4. Soft Limits ✅
     - These never worked on our machine. We don't know why. We just don't use them.
      ### **FIX**
       - Don't use
  5. Weird GCode ✅
     - There are a few weird little GCode quirks that we have to deal with to operate. Shown here is what the start and end of our GCode looks like. This works. Obviously it will be different depending on position, tool, etc but the start and end remain the same. Make sure your code looks similar/the same, as you run the risk of breaking a bit if not. If it looks different, I'd suggest running the code without a bit, to ensure nothing will break before cutting.
### START
```
  (10022) # Program number (Changes)
  G90 G94
  G17
  G21
  (Ramp1) #This will be different depending on your action
  T1
  S5000 M3
  G17 G90 G94
  G54
  G0 Z15 #This is critical. This MUST be before the following line. This retracts the toolhead BEFORE moving XY
  G0 X-28.057 Y-2.102 # this changes
```
### END
```
G0 Z15
    # Usually there is an extra line here. Make sure to delete that, as it homes the machine, which can break bits. 
M30
```
  ### **FIX**
  - Change GCode every time. You could also write a program to do this. We will share that if we end up doing this.

## Assembly 🪛

  There is no strict assembly guide for this machine. We tried to document roughly our steps in the videos on our channel, but there are a lot of nuances and tricks needed that simply arent documented. Be prepared for sanding, and some weird assemblies. In order to cut aluminium, we had to manually machine multiple parts, such as the Z axis plates, the entire aluminium base of the buildplate, and the Z traveller mount. We do not recommend this for entry level builds. If you have some time, a 3D printer, and some experience in the STEM/3D printing fields, this is very doable. All of the parts we used are in the BOM, and if you follow the 3D model, it should be pretty straight forward. It took us a total of 35 hours to build this machine, but we were doing other things and not 100% focused for much of it, in addition to having to test multiple parts. If you have questions, reach out to us via youtube, or create an issue here. We recommend looking at some youtube tutorials for parts you don't quite understand. There are great ones which let us teach ourselves GRBL and Fusion 360 manufacturing/slicing. 

  A few notes.
  - Screws are mostly M4. The rails use M5x16 screws, and there are a few random M3 screws in there, but the majority are M4.
  - 

### CAD Models:
  [Found Here](https://github.com/AugGrauer/CNCMachine/tree/c9973d6ad02c3cf29ccf315ba2bd43aa739bddab/3D%20Models)
  
  Our CAD models are categorized by:
  - Imports (This is largely just parts we used to build the machine)
  - Parts (Actual parts we made which were either machined or cut)
  - Assemblies (Larger models, such as the Base and Z axis)
  
### Wiring:
[Found Here](https://github.com/AugGrauer/CNCMachine/tree/c9973d6ad02c3cf29ccf315ba2bd43aa739bddab/Wiring)

  We have provided our wiring diagram above. We also created a custom electrical box for these wires, but that is entirely optional. See docs in wiring folder for more info. 
  
### Firmware/Software:
  This machine runs off of GRBL and Universal GCode Sender. Below are the downloads:

  [GRBL](https://github.com/grbl/grbl)

  [UGS](https://winder.github.io/ugs_website/)

  We changed our GRBL config file before uploading to the Arduino. Make sure to get all the pin numbers correct. (Found in cpu_map.h)
  
  For UGS, we did not change much. Go through the Setup Wizard and ensure your machine passes all checks. Be sure to test limit switches and tune steps/mm for the steppers.

### Putting it all together:
  When it comes down to it, theres a few key steps to follow:
  
1. Order/Print parts
2. Assemble hardware
3. Wire based off of our guide
4. Flash GRBL
5. Troubleshoot and Test UGS

There is no exact guide (Yet?) but if you have questions, please create an issue here, leave a comment on our videos, or even email us.

Here is the link our video playlist explaining it: https://www.youtube.com/watch?v=x9RqWOT4NOQ&list=PLWdkqCAyfFqSBZGNOKGVb3XG4A6ohDbLp

## Media

[Images here]

## Contributing 🔨
  We welcome any progress, changes, and suggestions. We definitely want to improve and build upon both this machine and open source project.

## Roadmap
  - Design Dust collection/cleaning system
  - Automate spindle cooling/oil dripping
  - Explore VFD possibilites
  - Create a GCode Pre-processor to speed up work

## Changelog
  # V 1.0
  - Initial open-source release
  - Complete with BOM, CAD models, wiring diagrams, and build videos
