# CNCMachine
Open source repository for the CNC machine built by Backyard Shed Engineering (https://www.youtube.com/@ShedStuffBuiltHere)



## Specifications
  Buildplate: 16x18x1 in 
  
  Capable of cutting 6061 Aluminium and softer.
  
  120V Power
  
  Total Size:
## BOM
BOM is in repository and also here:
https://docs.google.com/spreadsheets/d/1JcS2ukq2nQpIpGEV6_Kvxhg6B4QogmMNbcgQQ2et4MQ/edit?usp=sharing

# Use
  We have created this repository in order to make our CNC project as open source as possible. We were really proud to do this project for under $1000, and we want others to be able to as well. Feel free to use this as a basis to design your own, or to simply make your own version of our machine. We have included the BOM, all of our 3D models used, and our wiring diagram, as well as a few extra resources and our advice. We have further explanations on our youtube channel. ⏯️

## Known Issues
  This machine is by no means perfect, so there are a few problems we have encountered. Below is a list of the problems and if we have found solutions
  1. Electromagnet Interference: ✅
     - This is probably the largest issue encountered during construction and inital operation. After investigating, it turns out that our buildplate, and most metal on the body of the CNC machine is actually charged. We aren't sure why or from where, but we suspect that it is something to do with our stepper motors.
     ### **FIX**
       - To fix this, we used EMI shielding along most of the long wires which run from stepper motors to the electrical box. This is included in the BOM, and we had jsut enough to get most of our wires shielded. We found that there were a few specific areas which were worse, especially where the EMI shielding/ wires in general come in contact with the metal frame of the machine. We solved this by insulating those specific areas with electrical tape.
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

## Assembly
  There is no strict assembly guide for this machine. We tried to document roughly our steps in the videos on our channel, but there are a lot of nuances and tricks needed that simply arent documented. Be prepared for sanding, and some weird assemblies. In order to cut aluminium, we had to manually machine multiple parts, such as the Z axis plates, the entire aluminium base of the buildplate, and the Z traveller mount. We do not reccomend this for entry level builds. If you have some time, a 3D printer, and some experience in the STEM/3D printing fields, this is very doable. All of the parts we used are in the BOM, and if you follow the 3D model, it should be pretty straightfoward. It took us a total of 35 hours to build this machine, but we were doing other things and not 100% focused for much of it, in addition to haivng to test multiple parts. If you have questions, reach out to us via youtube, or create an issue here. We recommend looking at some youtube tutorials for parts you don't quite understand. There are great ones which let us teach ourselves GRBL and Fusion 360 manufacturing/slicing. 
  
  - Screws are mostly M4. THe rails use M5x16 screws, and there are a few random M3 screws in there, but the majority are M4.
