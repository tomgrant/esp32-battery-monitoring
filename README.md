# esp32-battery-monitoring
Monitor a connected battery voltage and percentage with an ESP32 for communicating with Home Assistant. 
This can be useful when powering an esp32 off a 18650 or similar, as I have done in this case.



It is important to note that not all pins on an esp32 are capable of `adc`, but generally pins 32-36 do. It is also worth noting that the voltage monitor cannot measure over 1 volt. So you will need to make use of a voltage divider. The calculation for the voltage in the middle of the voltage divider is `V R x = V i n ( R x R T )`

In my case, I'm using a single cell, so my input voltage reaches a maximum of 4.2v. I was able to reach under 1v with a 100kΩ and 10kΩ voltage divide. The voltage between them was then connected to pin 34. Your voltage divider configuration may vary, but my expected divided voltage was 0.382v. To then transform this to the real value for the calculation I multiplied it by 11.0994, which you will see in the filters.

![image](https://github.com/tomgrant/esp32-battery-monitoring/assets/1542257/8dab6d70-c35e-46fc-834e-52270d354b04)
