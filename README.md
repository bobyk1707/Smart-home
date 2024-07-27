# Smart-home
//A smart home with smart dustbin using arduino programming and devices.


# Smart Home Setup Project

This project demonstrates a simple smart home security system using an Arduino, a keypad, and a servo motor. The system allows users to unlock and lock a door using a predefined password entered through a keypad. Upon entering the correct password, a servo motor moves to unlock the door, and LEDs indicate the lock/unlock status.

## Components Required

1. Arduino Uno
2. 4x4 Keypad
3. Servo Motor (SG90 or similar)
4. LEDs (Red and Green)
5. Resistors (220 ohms)
6. Jumper Wires
7. Breadboard

## Circuit Diagram

1. **Keypad Connections:**
   - R1 (Row 1) -> Pin 9
   - R2 (Row 2) -> Pin 8
   - R3 (Row 3) -> Pin 7
   - R4 (Row 4) -> Pin 6
   - C1 (Column 1) -> Pin 5
   - C2 (Column 2) -> Pin 4
   - C3 (Column 3) -> Pin 3
   - C4 (Column 4) -> Pin 2

2. **Servo Motor Connection:**
   - Signal -> Pin 11
   - VCC -> 5V
   - GND -> GND

3. **LED Connections:**
   - Red LED anode -> Pin 12 (with 220-ohm resistor in series)
   - Green LED anode -> Pin 13 (with 220-ohm resistor in series)
   - Both LED cathodes -> GND

## Code Explanation

### Libraries Used
- `Keypad.h`: To interface with the 4x4 keypad.
- `Servo.h`: To control the servo motor.

### Global Variables
- `Servo ServoMotor`: Creates a servo object.
- `char *password = "123"`: Stores the predefined password.
- `int position = 0`: Keeps track of the current position in the password sequence.
- `const byte ROWS = 4, COLS = 4`: Defines the dimensions of the keypad.
- `char keys[ROWS][COLS]`: Stores the characters corresponding to each key.
- `byte rowPins[ROWS]`, `byte colPins[COLS]`: Maps the rows and columns of the keypad to the Arduino pins.
- `Keypad keypad`: Creates a keypad object.
- `int RedpinLock = 12, GreenpinUnlock = 13`: Defines the pins connected to the Red and Green LEDs.

### Setup Function
- Initializes the serial communication at 9600 baud rate.
- Sets the pin modes for the LEDs.
- Attaches the servo motor to pin 11.
- Calls `LockedPosition(true)` to set the initial locked state.

### Loop Function
- Continuously reads the key pressed on the keypad.
- Resets the position if `'*'` or `'#'` is pressed.
- Checks if the key pressed matches the current position of the password.
- Unlocks the door if the password is entered correctly by calling `LockedPosition(false)`.

### LockedPosition Function
- Controls the LEDs and the servo motor based on the locked/unlocked state.

## How to Use
1. Assemble the components as per the circuit diagram.
2. Upload the code to the Arduino Uno.
3. The system starts in the locked state.
4. Enter the password (`123` by default) using the keypad.
5. The servo motor will move to unlock the door, and the Green LED will turn on.
6. Press `'*'` or `'#'` to reset the system and lock the door again.

## Customization
- **Change Password**: Modify the `password` variable in the code to set a new 3-digit password.
- **Servo Positions**: Adjust the angles in the `ServoMotor.write()` calls within the `LockedPosition` function to suit your specific servo motor and door mechanism.

## Troubleshooting
- Ensure all connections are secure and correct as per the circuit diagram.
- Verify that the correct pins are defined in the code.
- Check that the keypad and servo motor are functioning properly.

## License
This project is open-source and available for modification and redistribution. Feel free to use and adapt it for your own smart home security needs.

## Author
- [Your Name]
- [Your Contact Information]

## Acknowledgments
Special thanks to the open-source community and various online resources for providing guidance and inspiration for this project.
