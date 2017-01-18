# Inital-program
The start drive train.
#include "WPILib.h"
#include "simpleCRobot.h"
static const UNIT32 LEFT_MOTOR_PORT = 1;
static const UNIT32 RIGHT_MOTOR_PORT = 2;
static const UNIT32 JOYSTIC_PORT = 1;

void Initialize(void)
{
    CreateRobotDrive(LEFT_MOTOR_PORT, RIGHT_MOTOR_PORT);
    SetWatchdogExpiration(0.1);
}
 
void Autonomous(void)
{
    SetWathdogEnabled(false);
    Drive(0.5, 0.0);
    Wait(2.0);
    Drive(0.0, 0.0);
}
 
void OperatorControl(void)
{
    SetWatchdogEnabled(true);
    While (isOperatorcontrol())
    {
      WatchdogFeed();
      ArcadeDrive(JOYSTICK_PORT);
    }
}

START_ROBOT_CLASS(SimpleCRobot);
