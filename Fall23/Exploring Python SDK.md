Goals:
During this semester the group's goal early on was to get ROS working but once I found out that the possibility of that happening for me 
was not feasible I decided to turn my focus onto python SDK (set development kit). The purpose of this was just to have an easy environment 
to work with the NAO bots. After turning my attention to the python SDK I also had the goal of creating a simple program to run through my 
terminal.

Process:
In the beginning of the semester, along with the rest of my peers, I worked on getting a VM (virtual machine) onto my computer with the 
intention of getting ROS (robot operating system) working on my laptop. Unfortunately, this did not work for me for a number of reasons. 
The first hiccup I ran into was that the M1 chip in my macbook made it so that the standard VM environment VirtualBox was incompatible with 
my macbook. In order to fix this I decided to use a UTM which is used to host VM’s specifically for IOS and mac OS users. Although I had to 
fiddle around with the settings a lot I did get the UTM to work. After my success I followed instructions given by my 
supervisor, Lisa J. Miller, to get ROS up and running on my UTM and it still did not work. I am still not sure why it didn’t work. In 
light of this failure Lisa brought up a different method for working with the NAO bots which is the python SDK. So I tried to install it 
onto the UTM and it did not work. But Lisa explained to me that the UTM I was using may have been acting as another wall that was blocking 
me from connecting to the NAO bots easily. Like in order to connect to the NAO bots instead of just going from a terminal to the KCC wifi 
and then to the NAO bots it was now like it was going from the terminal in my vm to my laptop to the KCC wifi and then to the NAO bots. 
This told me that I should try to install python SDK onto my mac OS terminal and once I did that, python SDK worked! I had no more issues 
after that when trying to connect to the NAO bots and I was even able to run some code that I found on the softbanks website that could 
make NAO do small things like speak and move around. At this point, while the NAO bots were able to walk around and talk I had to type in 
each line of code one by one in order to actually make this happen which was very annoying to do. Then Lisa presented the idea that maybe I 
could write up a program that I can call to run through my terminal so that I wouldn’t have to type everything out by myself and I could 
run commands automatically. I figured out that I  can do it using both VS code and TextEdit. TextEdit is an application specifically for 
mac OS while VS code had to be downloaded separately. So with either application all I needed to do was write my code/write the program and 
then save my file as a .py python file which was a lot more streamline for me using TextEdit. Basically it was simpler and had less steps. 
Here is a file that I created using TextEdit:
import naoqi
from naoqi import ALProxy
robot_ip = "192.168.0.244"
tts = ALProxy("ALTextToSpeech", robot_ip, 9559)
import qi
import time
import sys
import argparse


class HumanGreeter(object):
    """
    A simple class to react to face detection events.
    """

    def __init__(self, app):
        """
        Initialisation of qi framework and event detection.
        """
        super(HumanGreeter, self).__init__()
        app.start()
        session = app.session
        # Get the service ALMemory.
        self.memory = session.service("ALMemory")
        # Connect the event callback.
        self.subscriber = self.memory.subscriber("FaceDetected")
        self.subscriber.signal.connect(self.on_human_tracked)
        # Get the services ALTextToSpeech and ALFaceDetection.
        self.tts = session.service("ALTextToSpeech")
        self.face_detection = session.service("ALFaceDetection")
        self.face_detection.subscribe("HumanGreeter")
        self.got_face = False

    def on_human_tracked(self, value):
        """
        Callback for event FaceDetected.
        """
        if value == []:  # empty value when the face disappears
            self.got_face = False
        elif not self.got_face:  # only speak the first time a face appears
            self.got_face = True
            print "I saw a face!"
            self.tts.say("Hello, you! I am NAO!")
            # First Field = TimeStamp.
            timeStamp = value[0]
            print "TimeStamp is: " + str(timeStamp)

            # Second Field = array of face_Info's.
            faceInfoArray = value[1]
            for j in range( len(faceInfoArray)-1 ):
                faceInfo = faceInfoArray[j]

                # First Field = Shape info.
                faceShapeInfo = faceInfo[0]

                # Second Field = Extra info (empty for now).
                faceExtraInfo = faceInfo[1]

                print "Face Infos :  alpha %.3f - beta %.3f" % (faceShapeInfo[1], faceShapeInfo[2])
                print "Face Infos :  width %.3f - height %.3f" % (faceShapeInfo[3], faceShapeInfo[4])
                print "Face Extra Infos :" + str(faceExtraInfo)

    def run(self):
        """
        Loop on, wait for events until manual interruption.
        """
        print "Starting HumanGreeter"
        try:
            while True:
                time.sleep(1)
        except KeyboardInterrupt:
            print "Interrupted by user, stopping HumanGreeter"
            self.face_detection.unsubscribe("HumanGreeter")
            #stop
            sys.exit(0)


if __name__ == "__main__":
    parser = argparse.ArgumentParser()
    parser.add_argument("--ip", type=str, default=robot_ip,
                        help="Robot IP address. On robot or Local Naoqi: use " + robot_ip + ".")
    parser.add_argument("--port", type=int, default=9559,
                        help="Naoqi port number")

    args = parser.parse_args()
    try:
        # Initialize qi framework.
        connection_url = "tcp://" + args.ip + ":" + str(args.port)
        app = qi.Application(["HumanGreeter", "--qi-url=" + connection_url])
    except RuntimeError:
        print ("Can't connect to Naoqi at ip \"" + args.ip + "\" on port " + str(args.port) +".\n"
               "Please check your script arguments. Run with -h option for help.")
        sys.exit(1)

    human_greeter = HumanGreeter(app)
    human_greeter.run()
# Quit with Ctrl + C
When testing these programs my computer for some reason stopped recognizing a method called: ALTextToSpeech which is a method built into 
the NAO bot system. I was getting a runtime error for the method which is difficult to get rid of by nature. I don’t really understand what 
went wrong/how to fix it. After talking to Lisa about it she recommended updating the NAO bots but unfortunately we ran out of time this 
semester to do that.

Result:
For a short period of time I was able to successfully run these programs until they stopped working. For example, the program above was able
to greet someone if it got within a certain distance close to it which was pretty cool. 

For the next person:
If you have a macbook with the M1 chip in it and you wish to pursue working with the NAO bots outside of choreograph in my experience I 
suggest that you try working with python SDK. It seems more feasible for it to run successfully than ROS is, at least at this point in 
time, and creating a program is not too difficult. Also, the specific python language matters and I had to download python 2.7. Macbook
uses python 3 automatically so make sure that you have python 2.7 downloaded before using python SDK.
