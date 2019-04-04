# HeartBeatMonitor-Arduino

 We designed a Heart Beat Monitor using Arduino in Proteus ISIS.
 
 You should download this [Heart Beat Sensor Library V2.0](https://www.theengineeringprojects.com/2017/11/heart-beat-sensor-library-v2-0-for-proteus.html) for Proteus because it is used to detect heart beat in Proteus.
 
 We have also used a 20×4 LCD which will display our heart beat value. We have counted the heart beat for ten seconds and then We have multiplied it with 6 to get the heart beat per minute which is abbreviated as bpm (beats per minute).
 
 Steps:
 
 1. Download .hex files and remaining files from the repository.
 
 2. Design the circuit as shown here: 
                  ![circuit](/images/1.1.PNG)
                  
 
4. Download the code from repo.

5. In this code, We have used a TimerOne Library which creates an interrupt after every 1sec.

6. So, when TimeinSec will become equal to 10 then I am simply multiplying it with 6 and updating it on the LCD.

7. So, use the above code and get your Hex File from Arduino Software and update it in your Proteus Simulation.

8. Now run your Proteus Simulation, Now click this HB button and it will start counting the HB as well as will count the Time in seconds.

9. Change the value of variable resistance connected to Heart Beat sensor, to show different BPM at the results.

### This is simple demonstration of working of HeartBeat Monitor using Arduino UNO in Proteus ISIS.
