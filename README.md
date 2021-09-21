# Subsystem-
Display, LED and ADC subsystem


Part A 
Display Sub-systemInteracting with a user is one of the important features of an embedded system. Creating a 4threads and 2 interrupt service routines (ISRs).Thread1 will  manage  communications from the  PC to the K64F over the Virtual Communications Port(VCP) whilst Thread2 will manage communications from the K64F to the PC over the VCP.Thread1 will read text from the keyboard,echo them back  to  the  display via Thread2 and also  decode  any  valid  messages to signal to the other threads. Thread 2will read messages from a MailQueuewhere ascii strings of no more than 127 printable characters are  passed  through  the  Mail Queue
(NB: It is actually the pointer to the memory string  that  gets  passed  to  the  Mail Queue–check the notes on Mail Queues)The two ISRs will monitor the two switches SW2 (PTC6) and SW3(PTA4) and the 2 threads associated with the ISRs will send appropriate string messagesto Thread2via the Mail Queue when the status of any switch changes e.g. a message “SW2 pressed” or “SW2 released” should be displayed on the PC terminal.


Part B 
LED Sub-system now adding an extra thread,Thread5, that drives the value of the RGB LEDs when requested to by Thread1 when it receives the characters ‘r’, ‘R’, ‘g’, ‘G’, ‘b’ and ‘B’typed by the user.When the character is in lower case it should switch off the LED and when the character is in upper case it should switch on the LED.You should use signals to provide the mechanism for communications between Thread 1 and Thread5.


PartC 
ADC Sub-system now adding an extra two threads,Thread6, which reads the values of the ADC connected to Pot1 at a periodic rate which can be set by the user typing 1 followed by a space and the sample period in ms(i.e. 1 1000 would correspond to 1Hz sampling–use a default rate of 0.1 Hz until the new rate is received) and Thread 7, which reads the values of the ADC connected to Pot 2 when requested to by Thread 1 when it receives the character “2”. Again you should useSignals to communicate between Thread 1 and Thread7. Threads 6 and 7 should communicate the read values back to Thread2 via messages sent to the Mail Queue where the values are then displayed overthe VCP.You need to add an appropriate mechanism to stop Thread6 trying to use the ADC when Thread7 is using it and vice versa. Adding an extra threads/ ISRs to assist Thread6 adn to communicate the sample rate.
