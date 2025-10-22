# CyberWatch32
A digital watch made with a custom curcuit board and the STM32L0. Made to push the limits of low power wearable technology and my hardware skills

# The Original Project
This project originally started out as a very different project with the same goal. I started out with the CH32 Microprocessor, otherwise known as the 10 cent microcontroller. The first draft of this project used a real time clock, a 128px OLED display and the CH32. This would work in theory, but with the very limited RAM of the CH32 I was either going to have to get better at programming, or change the hardware.

# V2
The second revision changed to the much more powerful STM32L010K8, which is used in the final board. This version made it all the way to a finished PCB design and right before I exported it for production, I notcied a critical flaw in the power management (dont let ChatGPT read datasheets for you) and I decided that a third revision was needed. 

# The Current Design
The third and final design took a step back from the old project and aimed to do things correctly this time. Starting with a list of features, I wanted more than just a RTC. I specced out a new interital measurement unit and a magnetometer to give me a compass display. The biggest change however came from the power section. The design flaw from V2 comes from a concept known as powerpathing. the system runs on 3.3V, but USB is 5V and the LIPO battery is 3.7V my original design had no way to know what voltage is coming through and the components regulated them both the same, meaning the device would never work off of battery (you also can't just charge the battery with USB and always power off the battery, this is very dangerous and will harm the battery if you charge and discharge at the same time). The current design uses new power componenents to individually protect, charge, and regulate the power to provide a stabel and clean 3.3V all of the time.
https://github.com/Kacman62/CyberWatch32/blob/main/images/CW32PowerSchematic.png?raw=true 
