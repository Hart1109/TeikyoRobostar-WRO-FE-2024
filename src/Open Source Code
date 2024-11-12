import cv2
import os
import numpy as np
import time
import threading
import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
from buildhat import Motor, DistanceSensor, ColorSensor

motorBack = Motor('D')
motorFront = Motor('C')
distLeft = DistanceSensor('A', threshold_distance=100)
distRight = DistanceSensor('B', threshold_distance=100)
GPIO.setup(18, GPIO.IN, pull_up_down=GPIO.PUD_UP)

motorBack.stop()
motorFront.stop()

#Default setting
#Start speed
pw = -47
adjustment = 5

def setup():
    dist_L = distLeft.get_distance()#Stores distance to left wall
    dist_R = distRight.get_distance()#Stores distance to right wall
    motorFront.run_to_position(adjustment,blocking=False)
    print("standby")
    GPIO.wait_for_edge(18, GPIO.FALLING)
    time.sleep(0.3)
    
def setMotor():
    motorBack.set_default_speed(-pw)#Setting the motor speed of the rear wheels
    motorFront.set_default_speed(-pw)#Setting the motor speed of the front wheels

def run(pw):
    motorBack.start(pw)#Start speed setting

def stop():
    motorBack.stop()#Stops rear wheel movement
    motorFront.stop()#Stops front wheel movement

def runStraight():#Program to run horizontally against a wall
    if turnCount == 0:#When the direction is not set
        dif = dist_R - dist_L
        if (dif - firstDis < -10):
            motorFront.run_to_position(10,blocking=False)
            time.sleep(0.3)
        elif (dif - firstDis > 10):
            motorFront.run_to_position(-5,blocking=False)
            time.sleep(0.3)
    if rotation == "Left":#Counterclockwise rotation
        if dist_R < tDist - 10:
            motorFront.run_to_position(14,blocking=False)
            time.sleep(0.3)
        elif tDist - 10 <= dist_R and dist_R <= tDist + 10:
            motorFront.run_to_position(0,blocking=False)
            time.sleep(0.3)
        elif tDist + 10 < dist_R:
            motorFront.run_to_position(-6,blocking=False)
            time.sleep(0.3)
            
    if rotation == "Right":#Clockwise rotation
        if dist_L < tDist - 10:
            motorFront.run_to_position(-8,blocking=False)
            time.sleep(0.3)
        elif tDist - 10 <= dist_L and dist_L <= tDist + 10:
            motorFront.run_to_position(0,blocking=False)
            time.sleep(0.3)
        elif 250 <= dist_L:
            motorFront.run_to_position(14,blocking=False)
            time.sleep(0.3)
            
def backTurn():#Backward program
    if rotation == "Left":#Counterclockwise rotation
        motorFront.run_to_position(0,blocking=False)
        motorBack.run_for_degrees(360,-pw)
        motorFront.run_to_position(30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(50,pw)
        motorFront.run_to_position(30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(2050,pw)
        time.sleep(0.3)

    elif rotation == "Right":#Clockwise rotation
        motorFront.run_to_position(0,blocking=False)
        motorBack.run_for_degrees(360,-pw)
        motorFront.run_to_position(-30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(50,pw)
        motorFront.run_to_position(-30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(1800,pw)
        
def turn():#Turning the corner program
    if rotation == "Left":#Counterclockwise rotation
        motorFront.run_to_position(30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(50,pw)
        motorFront.run_to_position(30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(2050,pw)
        time.sleep(0.3)
        
    elif rotation == "Right":#Clockwise rotation
        motorFront.run_to_position(-30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(50,pw)
        motorFront.run_to_position(-30, blocking=False)
        time.sleep(0.2)
        motorBack.run_for_degrees(1800,pw)
      
#Enter initial values for each variable
x = 0
y = 0
finishCount = 0#Used during the finish section
allowRun = True#Determine if it is running or not.
turnCount = 0#Measure the number of times a corner is turned
rotation = ""
tDist = 0
turnWait = 0
backJudge = 200

#Mainprogram
setMotor()
setup()
while True:
    dist_L = distLeft.get_distance()#Stores distance to left wall
    dist_R = distRight.get_distance()#Stores distance to right wall
    
    if allowRun:
         run(pw)
    else:
        stop()
        break
    
    if x == 0:
        firstDis = dist_R - dist_L
        x += 1

    if rotation == "":
        runStraight()
        if dist_L < 0 or 1200 < dist_L:#If the left sensor cannot recognize the distance
            rotation = "Left"
        elif dist_R < 0 or 1200 < dist_R:#If the right sensor cannot recognize the distance
            rotation = "Right"
            
    if rotation == "Left":#Counterclockwise rotation
        if turnCount >= 12:#When you turned the corner 12 times
            if finishCount < 5:#If the count is 5 or more
                runStraight()
                finishCount += 1
            else:
                allowRun = False#If the count is less than 5
                print("stop")
                
        if (0 < dist_L and dist_L < 1200):#If the left sensor can recognize the distance
            turnWait = 0
            backJudge = dist_L
            runStraight()
            if y > 0:
                y -= 1
                
        if (dist_L < 0 or 1200 < dist_L):#If the left sensor cannot recognize the distance
            turnWait += 1
            if (y == 0) and turnWait == 2:
                print("turning")
                if backJudge < 120:#When the distance from the wall is close
                    turn()
                else:
                    backTurn()#When the distance from the wall is far
                tDist = distRight.get_distance()
                turnCount += 1
                y += 5
            else:
                runStraight()

    elif rotation == "Right":#Clockwise rotation
        if turnCount >= 12:#When you turned the corner 12 times
            if finishCount < 5:#If the count is 5 or more
                runStraight()
                finishCount += 1
            else:
                allowRun = False#If the count is less than 5
                print('stop')
                
        if (0 < dist_R and dist_R < 1200):#If the right sensor can recognize the distance
            turnWait = 0
            backJudge = dist_R
            runStraight()
            if y > 0:
                y -= 1

        if (dist_R < 0 or 1200 < dist_R):#If the right sensor cannot recognize the distance
            turnWait += 1
            if (y == 0) and turnWait == 2:
                print("turning")
                if backJudge < 120:#When the distance from the wall is close
                    turn()
                else:
                    backTurn()#When the distance from the wall is far
                tDist = distLeft.get_distance()
                turnCount += 1
                y += 5
            else:
                runStraight()
　　#Displays the value of each variable
    print(f"dL:{dist_L} dR:{dist_R} aR:{allowRun} tD:{tDist} ro:{rotation} count:{turnCount} y: {y} finish:{finishCount}")






