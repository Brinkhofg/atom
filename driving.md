import lejos.hardware.Sound;
import lejos.hardware.lcd.LCD;
import lejos.utility.Delay;
import lejos.hardware.motor.EV3MediumRegulatedMotor;
import lejos.hardware.port.MotorPort;
import lejos.robotics.RegulatedMotor;


public class Driving {
 private Robot wall_e;
 static RegulatedMotor motorD = new EV3MediumRegulatedMotor (MotorPort.D);

 public Driving(Robot wall_e) {
  this.wall_e = wall_e;
  wall_e.getPilot().setLinearSpeed(150);
  wall_e.getPilot().setAngularSpeed(100);
  wall_e.getPilot().setAngularAcceleration(50);
  wall_e.getPilot().setLinearAcceleration(30);
 }


public void rotBlau(float test) {
  if (test ==0) {
  wall_e.getPilot().travel(400);
  wall_e.getPilot().rotate(90);
  wall_e.getPilot().travel(300);
  
  motorD.rotate(-80);
  Sound.beep();
  wall_e.getPilot().travel(-300);
  motorD.rotate(80);
  
  wall_e.getPilot().rotate(-90);
  wall_e.getPilot().travel(-400);
 }else {
  wall_e.getPilot().travel(400);
  wall_e.getPilot().rotate(-90);
  wall_e.getPilot().travel(300);
  
  motorD.rotate(-80);
  Sound.beep();
  wall_e.getPilot().travel(-300);
  motorD.rotate(80);
  wall_e.getPilot().rotate(90);
  wall_e.getPilot().travel(-400);
 }

 
}
 private float driveBlock(float farbe) {
  float[] colorID =wall_e.getColorSample();
  
  
  motorD.rotate(-80);
  wall_e.getPilot().travel(340);
  motorD.rotate(80);
  wall_e.getPilot().travel(-100);
  wall_e.getPilot().travel(100);
  for (int i=0; i<=100;i++) {
   colorID = wall_e.getColorSample();
   farbe=colorID[0];
   Delay.msDelay(10);
   } 

  wall_e.getPilot().travel(-340);


  return farbe;
}
 private float driveBlock1(float farbe) {
	  float[] colorID =wall_e.getColorSample();
	  
	  
	  motorD.rotate(-80);
	  wall_e.getPilot().travel(360);
	  motorD.rotate(80);
	  for (int i=0; i<=100;i++) {
	   colorID = wall_e.getColorSample();
	   farbe=colorID[0];
	   Delay.msDelay(30);
	   } 
	  wall_e.getPilot().travel(-360);


	  return farbe;
	}

public void drivecourse() {
	
float farbe =-1;
  motorD.setSpeed(100);
  LCD.clear();
  wall_e.getPilot().travel(148);
  wall_e.getPilot().rotate(-90);
  farbe=driveBlock(farbe);
  wall_e.getPilot().rotate(90);
  wall_e.getPilot().travel(550);
  wall_e.getPilot().rotate(90);
  rotBlau(farbe);
  
  
  wall_e.getPilot().rotate(90);
  wall_e.getPilot().travel(280);
  wall_e.getPilot().rotate(90);
 farbe= driveBlock(farbe);
  wall_e.getPilot().rotate(-90);
  wall_e.getPilot().travel(-280);
  wall_e.getPilot().rotate(-90);
  rotBlau(farbe);
  
  wall_e.getPilot().rotate(180);
  farbe=driveBlock(farbe);
  wall_e.getPilot().rotate(-180);
  rotBlau(farbe);
  
  wall_e.getPilot().rotate(-90);
  wall_e.getPilot().travel(290);
   wall_e.getPilot().rotate(-90);
  farbe=driveBlock(farbe);
  wall_e.getPilot().rotate(90);
   wall_e.getPilot().travel(-290);
   wall_e.getPilot().rotate(90);
   rotBlau(farbe);
   
   
   wall_e.getPilot().rotate(-90);
   wall_e.getPilot().travel(590);
   wall_e.getPilot().rotate(-90);
   wall_e.getPilot().travel(10);
  farbe= driveBlock(farbe);
    wall_e.getPilot().rotate(90);
    wall_e.getPilot().travel(-590);
    wall_e.getPilot().rotate(90);
    rotBlau(farbe);
}
}
