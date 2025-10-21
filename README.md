

##  Introduction
This project implements a **24-hour digital clock with alarm functionality** using **Verilog HDL**.  
It provides **7 output signals**: hour, minute, second digits, and an alarm signal.  
The clock can be initialized to a specific time and alarm can be set or disabled.  
The input clock is **10 Hz**, from which a **1-second clock** is derived to increment time accurately.

## Flow Chart
![](https://github.com/arjunrpai/Alarm-Clock-using-FPGA/blob/main/flowchart.png)


##  Features
- 24-hour time format display (HH:MM:SS)  
- Manual time initialization (`LD_time`)  
- Configurable alarm (`LD_alarm`)  
- Alarm enable/disable control (`AL_ON`)  
- Stop alarm functionality (`STOP_al`)  
- Automatic time increment with proper rollover  
- Active-high reset for initializing clock and alarm

  
## Working Principle
- Generates a **1-second clock** from 10 Hz input.  
- Increments seconds, minutes, and hours with proper rollover.  
- Continuously compares current time with alarm time.  
- Triggers `Alarm` output when time matches and alarm is enabled.  
- Alarm stops when `STOP_al` is high.  



## Input Signals
| Signal     | Description |
|------------|-------------|
| `reset`    | Active-high reset. Sets time to `H_in1:H_in0:M_in1:M_in0:00` and alarm to `0:0:0`. |
| `clk`      | 10 Hz input clock used to generate 1-second time base. |
| `H_in1`    | Most significant hour digit (0-2) for clock or alarm. |
| `H_in0`    | Least significant hour digit (0-9) for clock or alarm. |
| `M_in1`    | Most significant minute digit (0-5) for clock or alarm. |
| `M_in0`    | Least significant minute digit (0-9) for clock or alarm. |
| `LD_time`  | Loads current time from inputs. |
| `LD_alarm` | Loads alarm time from inputs. |
| `AL_ON`    | Enables/disables alarm. |
| `STOP_al`  | Stops alarm when high. |


## Output Signals
| Signal     | Description |
|------------|-------------|
| `Alarm`    | High when current time equals alarm time and `AL_ON=1`. |
| `H_out1`   | Most significant hour digit (0-2). |
| `H_out0`   | Least significant hour digit (0-9). |
| `M_out1`   | Most significant minute digit (0-5). |
| `M_out0`   | Least significant minute digit (0-9). |
| `S_out1`   | Most significant second digit (0-5). |
| `S_out0`   | Least significant second digit (0-9). |



