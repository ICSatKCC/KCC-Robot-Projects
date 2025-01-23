### Getting Started
Meet NAO, a humanoid robot, created by Softbank Robotics! 

<img src="https://provenrobotics.ai/wp-content/uploads/2022/06/nao.webp" height="200" width="180" >

I recommend getting familiar with NAO first before programming it. The Softbank Robotics Documentation can be found [here.](http://doc.aldebaran.com/2-8/getting_started/index.html)

(Note: The company was doing a restructuring this semester so by the time you are reading this, they might have a new website up.)

* After turning NAO on (by pressing the chest button), this [link](http://doc.aldebaran.com/2-8/family/nao_user_guide/basic_channel_conversation_nao.html#bchannel-text-nao) contains everything you can say to NAO like asking NAO to sing "Mary had a little lamb." 

* On Youtube, if you search "NAO robot," there are many videos on what people had program NAO to do. These are short videos which shows NAO picking up an item and throwing it in a trashcan, NAO doing Gangnam Style, etc. This [link here](https://funlab.nd.edu/the-nao-base/special-movements/) shows other examples, like NAO doing pushups and various types of dances. Initially, I wasn't sure on what I wanted to program, so doing this helped me a lot!
---
### What you Need to Download 
**Note: If you plan to use the KCC laptop, you can bypass this step! Unfortunately, right now, Choregraphe is not compatible on the newer MACs :disappointed:**

If you plan to work on your project at home, this is what you need to download on your computer (sorry, I would insert links but because the company is currently doing a restructring as I am writing this, I can't seem to find a working link):

* **Choregraphe** (the desktop application that allows you to program NAO, basically the GUI. Choregraphe also allows you to connect to a virtual robot, so you can work on your project at home & test out your project to an extent) 

* **Robot Settings** (the desktop application that must be install to connect to NAO. Make sure NAO is connected to the same network as your computer)
---
### How to Use Choregraphe
**We had a Zoom Choregraphe training that was recorded, so I recommend watching that first on Laulima before getting started!**

There are two ways to program NAO using Choregraphe:

1) Drag and drop actions from the box libraries on the left into the middle window, creating a flow diagram. This is very similiar to the Scratch program. 
2) Create your own boxes in Choregraphe and write your code in Python (NAO is supported in other languages like Java and C++ but I recommend using Python since the preprogrammed box libraries are written in Python) 

Note: I read there is a way to program NAO without using Choregraphe at all using only Python (however, I could not get that to work on my computer)  

---
### The Holy Grail Help Document I Wish I Found Sooner!! 
I highly recommend going through this [website](https://www.kramirez.net/Robotica/Material/Nao/AnIntroductionToRoboticsWithNao_TextBook_2012_US.pdf)! I wish I found this sooner! 

Even though this help doc is a bit long, it is split into 10 modules that shows you different things you can do with NAO, using the preprogrammed box libraries and using Python. It also goes over the timeline feature in Choregraphe.

---
### Other Helpful Resources 
1) https://www.youtube.com/watch?v=zmsg1l6d5fc&ab_channel=RobotLABInc.

* This video taught me how to create my own boxes on Choregraphe and briefly goes over what the default Python functions mean. It also goes over some basic examples, like how you can change the parameters to make NAO walk in a circle.

2) https://www.youtube.com/watch?v=Djzb8c41qbk&ab_channel=PhilipEnglish

* There are three shorter videos on this channel that go over the basics on how to program NAO using Python.

3) http://doc.aldebaran.com/2-5/naoqi/index.html

* If you were interested in writing code, NAOqi is the name of the main software that runs on NAO and controls it. This website contains the list of all NAOqi APIs.
---
### What I Did
I wanted to explore the movement side of NAO, by trying to create a workout robot. The video of my robot can be found [here.](https://drive.google.com/file/d/1o-UEUa4wZKuBbXlWJKfr-SBzI9l-h0dT/view?usp=sharing)

Basically, I had NAO stand up, raise its arms and walk in different directions. Then, I had NAO move its arms and sit back down. My program was a mixture of using the preprogrammed boxes in Choregraphe and creating my own boxes in Python. The two NAOqi APIS I used were ALMotion and ALTextToSpeech. 

---
### Final Thoughts
* I would like to emphasize going through this [website!](https://www.kramirez.net/Robotica/Material/Nao/AnIntroductionToRoboticsWithNao_TextBook_2012_US.pdf) I wish I found this sooner because it was very helpful for me. 

* Start early 😭! There are so many things you can do with NAO so I wish I started earlier & be sure to allow some time to troubleshoot/in case things don't go as plan. 

* Good luck & have fun!!


