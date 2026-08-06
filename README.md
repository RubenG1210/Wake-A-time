# Wake-A-time

I HATE standard alarm clocks, because they use a Loud noise to "Ensure" you dont oversleep, But I ALWAYS end up Oversleeping, or I get woken up so roughly that I have brain fog for the whole day or my morning is ruined. I wanted to make a more better way to slowly bring you out of sleep instead of the loud awakening.

Thats when I decided I need to make a project that can help me with this problem, See that when you use a alarm you get woken up so roughly that your blood pressure rises, and can eventually lead to chronic stress. Or Some just dont wake up at all.

One day, I woke up correctly on time, Not because of hearing the alarm, a internal clock, but because the alarm I had on my phone was creating haptic buzzing, since my phone was near me I was directly feeling the buzzing patterns, which slowly drew me out of sleep.

Thats how I knew what I had to build, that I had to replicate that same feeling, that same buzzing, that same feeling of peacefullness upon awakening.

# Usability

How would Wake-A-Time be used? Since making a wearable from complete scratch is a very hard and long process, I will take inspiration from other brands and build upon then. Thus, Wake-A-Time will be a wrist wearable. 

# MCU(Microcontroller Unit)

I wanted to choose a MCU Module, first I had to of course take the Original ESP32 Dev in accountability, but it would simple be too large for a Wrist. Then the ESP32 Supermini C3 came in mind, And I was about to choose it, Until I saw a simple ad for a XIAO ESP32 C3, At first I thought that the differences were low to none. Until upon further research the XIAO has a built in LIPO charger, which could save me both money and space. Final Decision is the XIAO.

# Modules 

As a first iteration of this, I will first begin testing on a breadboard before switching to a Perfboard, and as a final product, a PCB, but until then, I will use Modules. 

Before choosing any modules, you have to understand what you need, for this, it'll be simple, I need a Wrist Worn product that has accurate time, haptic feedback, and a screen to display wake up time or to change the settings.

Here's what I came up with. 

For accurate time, a RTC module is crucial, the most accurate time, with little to no drift would be the DS3231, lets leave this at the chip for now, Just remember that the RTC module needs the DS3231 chip.

For Haptic Feedback, We first need of course our vibration motors, although more importantly, the Haptic Driver, The most smallest, efficient and reliable driver that I could find is the DRV2605L, Restated, remember this chip.

Lastly for the Screen, I dont need anything complex, large, or colorful, but efficient and small, that's when the classic 0.96 inch SSD1306 OLED comes. 


Lets take a break, This project isn't just hardware and code, But it has to involve psychology and Humane Behavior due to the UI and how the haptic driver wakes you up. Since simply making a hard buzzing noise would instantly annoy the user and wouldn't be any different from a traditional alarm clock. Thus I will build upon large apps, such as slowly building up, using small haptic touches, that slowly become more faster and sharper, to draw the user outside of sleep. The UI, the UI is one of the most important parts of this, people simply wouldn't use it if the UI is too boring or complicated. Plus large social media companies, including games have a way to hook you, to getting yourself addicted by creating "Streaks" or "daily rewards"

After deeper thought, for example losing a 50 day streak due to not waking up or being sick or such, would create instead of joy, or a sense of pride, it would create a sense of distraught or in general sadness. To combat this, I will implement a different type of streak, but it'll be called "Days of the month" that goes 1/30 and so on, Also if a user doesn't wake up on time, the streak simply doesn't move, thus encouraging the user to keep going.

You may ask how do we know the user has woken up for the streaks, going back to the UI, you will have to input a 4 PIN number via tactile buttons. Why? Why instead of a simple snooze you may ask? I researched how the brain first wakes up, using RAS, which acts as a switch, RAS may be activated via Noise, Light and touch. Then your frontal cortex is in charge of gaining consciousness. 

This system is designed for your body to first wake up, logical coordinated movements(Entering the passcode) while also using you brain for memory recallation, lastly the constant buzzing makes your Brain want to stop the timer, all of this helps full awakening and when the passcode is inputted the streak goes up, a simple, yet effective method.

This brings up back to the BOM 

# BOM(Build Of Materials)
## Links will be at the bottom

- Seeed Studio XIAO ESP32C3

- Haptic Motor Driver

- Mini Vibration Motors

- 0.96 Inch OLED Display

- 200mAh LIPO

- Electrical Male and Female Connector Plug (These are to make the Battery a plug and play system, and easily replaceable)

- DS3231 Real Time Clock

- 4.7K Ω Resistor

- 3 Tactile Buttons, (I already have these)

# Total Cost x Shipping x Taxes = $80-90 depending on price fluctuations and shipping.

# Wiring 

I2C BUS (shared SDA/SCL rows):
- XIAO D4 -> SDA bus row
- XIAO D5 -> SCL bus row
- DS3231 SDA -> SDA bus row
- DS3231 SCL -> SCL bus row
- DRV2605L SDA -> SDA bus row
- DRV2605L SCL -> SCL bus row
- SSD1306 SDA -> SDA bus row
- SSD1306 SCL -> SCL bus row
- (Only add 4.7k pull-ups on SDA and SCL to 3V3 if none of your breakouts already have them)

RTC ALARM INTERRUPT:
- DS3231 SQW/INT -> XIAO D0

BUTTONS (switch to ground, INPUT_PULLUP in software):
- MODE button: one leg -> XIAO D1, other leg -> GND
- UP button: one leg -> XIAO D2, other leg -> GND
- DOWN button: one leg -> XIAO D3, other leg -> GND
  
LAYOUT TIP:
- Run one continuous perfboard/breadboard strip each for 3V3, GND, SDA, SCL along the board length

# Code

Please keep into accountability that this is a project in process, I yet do not have any code, Although with this current list, I will adapt and slowly build the code to be able to have a finished code.

# Diagram/Shematic

<img width="1470" height="956" alt="Screenshot 2026-08-05 at 11 11 17 PM" src="https://github.com/user-attachments/assets/f7d713ca-cb09-4a4e-af11-4cd36690e81e" />



# Links 

[XIAO](https://www.amazon.com/gp/product/B0B94JZ2YF/ref=ox_sc_act_title_8?smid=A1YP59NGBNBZUR&th=1)

[Haptic Motor Driver](https://www.amazon.com/gp/product/B083G1MCYZ/ref=ox_sc_act_title_7?smid=A2KRDQ1AI5Y5G6&psc=1)

[Vibration Motors](https://www.amazon.com/gp/product/B0B4SK8M1C/ref=ox_sc_act_title_6?smid=A2L2YSK9NV3SSU&th=1)

[OLED Display](https://www.amazon.com/gp/product/B0GBWXTR1Z/ref=ox_sc_act_title_5?smid=A3CX4TQNUXMB0L&th=1)

[200mAh Lipo Battery](https://www.amazon.com/gp/product/B0CKRC99K6/ref=ox_sc_act_title_4?smid=A39OKXP5I8EI3U&psc=1)

[Electrical Male and Female Connector](https://www.amazon.com/gp/product/B07FP2FCYC/ref=ox_sc_act_title_3?smid=ASGOPLX5TLJL1&th=1)

[DS3231 RTC](https://www.amazon.com/gp/product/B09KPC8JZQ/ref=ox_sc_act_title_2?smid=A2Z10KY0342329&th=1)

[4.7K Ω Resistor](https://www.amazon.com/gp/product/B0BR8MYNNC/ref=ox_sc_act_title_1?smid=A2XLLJ8HYD6SMA&th=1)



