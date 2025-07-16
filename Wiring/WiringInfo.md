#**HERE IS THE LINK TO THE WIRING DIAGRAM**

https://miro.com/app/board/uXjVIAJd17c=/?share_link_id=497290069318

##Use
  This wiring diagram is what is currently on our operating CNC machien that was covered in the videos. The wires are roughly color coded (Best I could do). Red is for +, Black is for GND. The rest are signal wires, but all of them should be different distinct colors. The large squares/boxes in the diagram represent WAGO connectors, with the largest being 5 wire connectors, and the smallest being 3 wire connectors. Let us know about any issues. The stepper motor wiring is the exact same for every single one. THe funky wiring for the Z stepper motor ground is just a product of us not having enough WAGOs. To power the Arduino, we used a male DC power jack to the Arduino input. 

##GRBL Pins
  We used GRBL 1.1 for this machine. The pins on the arduino need to be configured to your specfic setup. This is found in config.h, which you should edit before pushing to the arduino. There are many tutorials online on how to use/upload GRBL. 
  
##Makita Router
  In order to make it work with a Makita router, we also added a grounding strap, which was simply one wire connected to an open WAGO ground port, which we stuck the other end into a grounded rod. Another wire was connected to the other open ground port, from there it has a Y-lead to ground both the router and the buildplate. 
