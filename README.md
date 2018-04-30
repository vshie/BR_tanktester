# BR_tankTester
python for controlling ESC, logging power supply &amp; force sensor
Usage of tanktester script:


From local keyboard


To launch script, run:;


(1) sudo screen -dmS tanktester /home/pi/tankinator/./tanktester.py


(2) sudo screen -r


Follow on-screen prompts - give a descriptive name to test (date and start time will be added automatically.) Choose a run-time (in seconds) for each throttle level to be tested. Finally choose the number of steps from 0 to 100% throttle (i.e. 10 would result in 10% throttle increments.) 


From remote keyboard


Using an ssh client (putty or similar on windows, terminal on mac/linux)


(3) ssh pi@tankinator.local


The password is companion - which is default for companion ROV pi image. Once logged in, run


(4) sudo screen -d -r


to be connected to the remote (already running) screen process.


Troubleshooting


“There is no screen to be resumed.” - Script running in screen has been closed or crashed. Re-launch with command (1) . If screen is still not available, launch just the script directly to see the error message:


(5)  /home/pi/tankinator/./tanktest.py


If error message contains
ACM1/ACM0 - Com port for Arduino has likely changed from 1 to 0 or vice versa.  Can happen if Arduino was unplugged for use on laptop or re-programming.


Editing functionality


The script has been structured to allow for several easy modifications. These variables are found in:
MAX_THROTTLE = 2000 #max must always be more than minimum. Swap motor wires to change direction!
MIN_THROTTLE = 1500
# These variables can be used to run test from 1100 to 1900 for one-direction only ESCs


settle_time = 40 # seconds between throttle steps. Change to input variable if frequently varied across tests
# Make this longer for higher quality data, especially if interested in powerful thrusters running at ludicrous power (>300w) for times greater than 7 seconds


loop_period = 0.1 # 1/ this = hz
# May run faster - but change Arduino Code corresponding value to output at same hz. (Dirty parsing code / rough sync.) Since pi is running on a much different architechture, time recorded can be observed to only approximate this timing. May run faster?


Remember - previous commands at terminal are found by pushing up arrow key, and can save a lot of typing!
