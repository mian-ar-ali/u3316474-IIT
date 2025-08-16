# 🐾 Automated Pet Feeder System

## 📘 Project Overview
This project presents a low-cost automated pet feeder system designed to dispense food twice daily, monitor whether the pet has eaten, and send SMS alerts to the owner under specific conditions. It integrates sensors, actuators, and communication modules to ensure reliable and intelligent pet care.

## 🛠️ Features
- Scheduled Feeding using a Real-Time Clock (RTC)
- Food Level Monitoring via Sonar Sensor
- Food Bowl Weight Detection using Load Cell
- Automated Dispensing with Servo Motor
- SMS Alerts via GSM Module
- Auto-Off Functionality for energy efficiency

## 📊 System Variables
| Variable        | Device         | Symbol       | Type   | Unit       | Sample Data | Notes |
|----------------|----------------|--------------|--------|------------|--------------|-------|
| Feeding Time    | RTC            | F-TIME       | Input  | HH:MM      | 08:00, 18:00 | 24-hour format |
| Food Tank Level | Sonar Sensor   | F-LEVEL      | Input  | cm         | 20 cm        | Measures distance to food surface |
| Bowl Weight     | Load Cell      | F-WEIGHT     | Input  | grams      | 10 gm        | Measures food weight in bowl |
| Dispense Food   | Servo Motor    | DISPENSE     | Output | Open/Close | Food Released | Dispenses 250 gm per feeding |
| User Alerts     | GSM Module     | ALERT_F-LEVEL, ALERT_F-WEIGHT | Output | SMS/Text | Alert messages | Sends SMS to owner |

## ⚙️ System Logic
1. System ON
2. Check Feeding Time
   - If F-TIME = FALSE, wait
   - If F-TIME = TRUE, proceed
3. Check Food Level
   - If F-LEVEL = FALSE (below 15 cm), send ALERT_F-LEVEL and skip feeding
   - Else, DISPENSE = TRUE
4. Wait 10 minutes
5. Check Bowl Weight
   - If F-WEIGHT = FALSE (≤ 150g), send ALERT_F-WEIGHT
   - Else, proceed
6. Check Auto-Off
   - If enabled, turn off system
   - Else, wait for next F-TIME = TRUE

## 🧪 Testing & Results
| Test Scenario           | F-TIME | F-LEVEL | F-WEIGHT | Expected Outcome                          | Actual Outcome                            |
|------------------------|--------|---------|----------|-------------------------------------------|-------------------------------------------|
| Not Feeding Time       | FALSE  | FALSE   | N/A      | No food dispensed                         | No food dispensed                         |
| Feeding Time, Low Level| TRUE   | FALSE   | N/A      | Alert sent, no food dispensed             | Alert sent, no food dispensed             |
| Feeding Time, Sufficient Level | TRUE | TRUE | N/A | Food dispensed | Food dispensed |
| Pet Did Not Eat        | TRUE   | TRUE    | FALSE    | Alert sent                                | Alert sent                                |
| Pet Ate Food           | TRUE   | TRUE    | TRUE     | No alert                                  | No alert                                  |

## 🚧 Limitations
- Fixed dispense amount (250 gm) may lead to food wastage.
- Missed feeding time if tank is refilled after scheduled time.
- No adaptive feeding based on pet consumption.

## 💡 Suggested Improvements
- Dynamic dispensing based on bowl weight

## 🤖 Use of AI
Microsoft Copilot AI was used to:
- Refine the word code logic
- Improve documentation structure
- Generate professional summaries and README content

## 🔗 Repository
[GitHub Repository](https://github.com/mian-ar-ali/u3316474-IIT)
