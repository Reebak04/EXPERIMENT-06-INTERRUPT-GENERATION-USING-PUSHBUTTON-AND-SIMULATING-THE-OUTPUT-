# EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT

### Aim:
To Interface a push button and generate an interrupt , simulate it using an led and simuate it on  proteus 

### Components required:
STM32 CUBE IDE, Proteus 8 simulator .

### Theory:

ARM v7 Core supports multiple great features for handling exceptions and interrupts. Which includes the Nested Vectored Interrupt Controller (NVIC).

Micro-Coded Architecture So that interrupt stacking, entry, and exit are done automatically in hardware. Which offloads this work overhead from the CPU
### Processor Mode

The processor mode can change when exceptions occur. And it can be in one of the following modes:
Thread Mode: Which is entered on reset.
Handler Mode: Which is entered on all other exceptions.
![image](https://github.com/vasanthkumarch/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/36288975/4f52f2d6-4cdb-4315-b2b2-b55dc1639c43)
The STM32 ARM microcontroller interrupts are generated in the following manner:

The system runs the ISR and then goes back to the main program. The NVIC and EXTI are configured. The Interrupt Service Routine (ISR) also known as the interrupt service routine handler is defined to enable the external interrupts.

Let us learn about the important features which are needed to configure external interrupts in STM32 microcontrollers

Interrupt Lines (EXTI0-EXTI15)
The STM32 ARM microcontroller features 23 event sources which are divided into two sections. The first section corresponds t external pins on each port which are P0-P15. The second section corresponds to RTC, ethernet, USB interrupts. Therefore, in the first section, we have 16 lines corresponding to line0 till line15. All of these map to a pin number.
The diagram below shows how the GPIO pins are connected to the 16 interrupt lines:

![image](https://github.com/vasanthkumarch/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/36288975/3e1ededb-144c-4103-a64e-9132b7e06e1b)

One important thing to note here is that same number pins are connected to line with the same number. All of these then join to form a single line. Additionally, we can not use two pins one one line at the same time. For example out of PA1, PB1, PC1, PD1, PE1, PF1 and PG1 you can only use a single pin out of all these. This is because they are all connected to the same line EXTI1. However you can use PA1 and PA2 at the same time as they are connected with different lines.

Now each of these lines EXTI0-EXTI15 can be used to trigger an interrupt on different modes of the signal : rising edge, falling edge or rising_falling edge.

## STM 32 CUBE PROGRAM :
```
Developed by : Tejusve Kabeer.F
Register no : 212222100054
void HAL_GIPO_EXTI_callback(uint16_t GPIO_Pin)
{
	if(GPIO_Pin == GPIO_PIN_0)
		{
		    HAL_GPIO_TogglePin(GPIOA,GPIO_PIN_1);
		}
}
```

## Output screen shots of proteus  :
 ### LED OFF :
![image](https://github.com/Reebak04/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/118364993/ac3d2446-fec9-4f39-a7d3-8ec2b561774a)

 ### LED ON :
 ![image](https://github.com/Reebak04/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/118364993/c75b1cd3-99ea-4ea9-99c9-59b347c47f68)

 ## CIRCUIT DIAGRAM : 
 ![image](https://github.com/Reebak04/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/118364993/983594ce-71ea-4130-869e-98c65360dff0)

 
## Result :
Interfacing a push button and interrupt genrateion is simulated using proteus 
