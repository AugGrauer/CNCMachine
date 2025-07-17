# CNCMachine
Open source repository for the CNC machine built by Backyard Shed Engineering (https://www.youtube.com/@ShedStuffBuiltHere)

## Use
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

#
