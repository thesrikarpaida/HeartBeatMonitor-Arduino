# HeartBeatMonitor-Arduino

 We designed a Heart Beat Monitor using Arduino in Proteus ISIS.
 
 You should download this [Heart Beat Sensor Library V2.0](https://www.theengineeringprojects.com/2017/11/heart-beat-sensor-library-v2-0-for-proteus.html) for Proteus because it is used to detect heart beat in Proteus.
 
 We have also used a 20×4 LCD which will display our heart beat value. We have counted the heart beat for ten seconds and then We have multiplied it with 6 to get the heart beat per minute which is abbreviated as bpm (beats per minute).
 
 Steps:
 
 1. Download .hex files and remaining files from the repository.
 
 2. Design the circuit as shown here: 
                  ![circuit](/images/1.1png)
                  
 3. As you can see in the above figure, we have our Arduino UNO board along with LCD and Heart Beat Sensor.
 
 4. There’s also a Button attached to Pin # 2, so when we press this button our Arduino will start counting the Heart Beat and will update  it on the LCD.
 
 5. Code: 
      ```
      #include <LiquidCrystal.h>
#include <TimerOne.h>
LiquidCrystal lcd(13, 12, 11, 10, 9, 8);

int HBSensor = 4;
int HBCount = 0;
int HBCheck = 0;
int TimeinSec = 0;
int HBperMin = 0;
int HBStart = 2;
int HBStartCheck = 0;

void setup() {
  lcd.begin(20, 4);
  pinMode(HBSensor, INPUT);
  pinMode(HBStart, INPUT_PULLUP);
  Timer1.initialize(800000); 
  Timer1.attachInterrupt( timerIsr );
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Current HB  : ");
  lcd.setCursor(0,1);
  lcd.print("Time in Sec : ");
  lcd.setCursor(0,2);
  lcd.print("HB per Min  : 0.0");
}

void loop() {
  if(digitalRead(HBStart) == LOW)
  {
	  lcd.setCursor(0,3);lcd.print("HB Counting ..");HBStartCheck = 1;
  }
  if(HBStartCheck == 1)
  {
      if((digitalRead(HBSensor) == HIGH) && (HBCheck == 0))
      {
        HBCount = HBCount + 1;
        HBCheck = 1;
        lcd.setCursor(14,0);
        lcd.print(HBCount);
        lcd.print(" ");
      }
      if((digitalRead(HBSensor) == LOW) && (HBCheck == 1))
      {
        HBCheck = 0;   
      }
      if(TimeinSec == 10)
      {
          HBperMin = HBCount * 6;
          HBStartCheck = 0;
          lcd.setCursor(14,2);
          lcd.print(HBperMin);
          lcd.print(" ");
          lcd.setCursor(0,3);
          lcd.print("Press Button again.");
          HBCount = 0;
          TimeinSec = 0;      
      }
  }
}

void timerIsr()
{
  if(HBStartCheck == 1)
  {
      TimeinSec = TimeinSec + 1;
      lcd.setCursor(14,1);
      lcd.print(TimeinSec);
      lcd.print(" ");
  }
}

      ```
