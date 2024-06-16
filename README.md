Components and Peripherals:
STM32 Microcontroller: The core of your system.
Analog Temperature Sensor: Reads the ambient temperature.
LCD Display: Shows the current temperature and mode status.
Relay: Controls an external device based on temperature thresholds.
Buttons:
Mode Selection (Auto/Manual)
Temperature Adjustment (in Manual Mode)
ADC (Analog-to-Digital Converter): Converts analog temperature readings to digital values.
I2C: Communicates with the LCD.
Key Variables:
autoMode: Indicates whether the system is in Auto Mode (1) or not (0).
manualMode: Indicates whether the system is in Manual Mode (1) or not (0).
adcValue: Stores the raw ADC value from the temperature sensor.
nhietdo: Calculated temperature from the ADC value.
dienap: Voltage corresponding to the ADC value.
count: User-set temperature threshold in Manual Mode.
set: Indicates if a temperature has been set in Manual Mode.
Initialization:
System Clock Configuration: Sets up the system clock.
Peripheral Initialization: Initializes GPIO, ADC, I2C, and LCD.
ADC Start: Begins ADC conversion to read temperature data.
LCD Initialization: Prepares the LCD for displaying information.
Main Functionality:
Mode Selection:
Auto Mode is selected by pressing a button connected to GPIO_PIN_12.
Manual Mode is selected by pressing a button connected to GPIO_PIN_15.
Temperature Setting:
In Manual Mode, the user can set a temperature threshold by pressing a button connected to GPIO_PIN_10.
Temperature Reading and Display:
Continuously reads the temperature in both modes.
Displays the current temperature on the LCD.
Relay Control:
In Auto Mode, the relay is activated if the temperature exceeds 45°C.
In Manual Mode, the relay is activated if the temperature exceeds the user-set threshold.
Interrupts:
HAL_GPIO_EXTI_Callback:
Handles button presses to switch modes and set temperature thresholds.
Updates the LCD based on mode changes and temperature settings.
Error Handling:
Error_Handler: Enters an infinite loop if an error occurs, disabling interrupts.
Functions:
SystemClock_Config: Configures the system clock.
MX_GPIO_Init: Initializes GPIO pins.
MX_ADC1_Init: Configures and initializes the ADC.
MX_I2C1_Init: Configures and initializes the I2C for LCD communication.
Main Loop:
In the main loop, the system:
Reads the temperature.
Updates the LCD with the current temperature.
Controls the relay based on the selected mode and temperature readings.
Delays for a short period before repeating.
