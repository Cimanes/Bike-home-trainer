# Bike-home-trainer
Speed and cadence sensors used to replicate a "bike computer" with Arduino

/*   Cimanes   30/04/2019
 *    
 *   Receive speed and cadence signals from a bike trainer 
 *   Use one "attachinterrupt" for speed singal.
 *   The "attachinterrupt" will trigger the speed calculations. 
 *   Cadence is not triggered with an attach interrupt, as it was causing unstable behavior. 
 *   Process the signal as a cycling computer (speed, cadence, pedals, distance, time, average speed/cadence)
 *   Serial print/plot the results
 *   Display results in LCD display
 *   Save results in a file on a SD card (Trainer.log).
 *   
 *   Original software has been designed to work with a "Tacx Fortius" bike trainer. 
 *   Digital inputs are configured as Input Pullup. Cadence signal is sampled in parallel to the Arduino and to the Fortius.
 *   Note: the Fortius cadence sensor uses voltage (0 VDC = constant) and (-5 VDC = pulses). 
 *   
 *   SD card attached to SPI bus as follows:
 *   MOSI     - pin 11 (UNO) / pin 51 (MEGA)
 *   MISO     - pin 12 (UNO) / pin 50 (MEGA)
 *   CLK      - pin 13 (UNO) / pin 52 (MEGA)
 *   CS or SS - pin 10 (UNO) / pin 53 (MEGA) / pin 4 (Ethernet Shield)
 *   
 *   MISO (Master In Slave Out) - The Slave line for sending data to the master,
 *   MOSI (Master Out Slave In) - The Master line for sending data to the peripherals,
 *   SCK / CLK (Serial Clock) - The clock pulses which synchronize data transmission generated by the master and one line specific for every device:
 *   SS (Slave Select) - the pin on each device that the master can use to enable and disable specific devices.
 *   
 *   On the Ethernet Shield, CS is pin 4. It's set as an output by default.
 *   Note that even if it's not used as the CS pin, the hardware SS pin (10 on most Arduino boards, 53 on the Mega) 
 *   must be left as an output or the SD library functions will not work. 
 *   
 *   LCD connection (LCD 1602 used):   
 *   {VSS VDD  V0 RS  RW  E D0 D1 D2 D3 D4 D5 D6 D7  A   K }
 *   {GND +5V POT 23 GND 25  -  -  -  - 27 22 24 26 +5V GND} 
 */
