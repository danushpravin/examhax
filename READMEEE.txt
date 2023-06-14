CYCLE-II : INTERFACING USING ARM STM32F401xx


    



A) Aim: To Write a C Program for Blinking of an LED on and off without delay.


Software Required: Keil μ Vision 5




#include"stm32F4xx_hal.h"
#include"Board_LED.h"
int main(void)
{
const unsigned intnum=0;
LED_Initialize();

while(1)
{
       LED_On(num);
       LED_Off(num);
}
}



RESULT :

The Program for Blinking of an LED ON and OFF without Delay is interfaced with board and outputs are
verified.




B) Aim: To Write a C Program for Blinking of an LED with delay using Set Out function.


Software Required: Keil μ Vision 5



#include"stm32F4xx_hal.h"
#include"Board_LED.h"
int main(void)
{
const unsigned intoff_code=0x0000;
        const unsigned inton_code=0x00ff;
        unsignedinti;
LED_Initialize();
{
for(;;)
        {
        for(i=0;i<30000;i++)
LED_SetOut(on_code);
        for(i=0;i<30000;i++)
LED_SetOut(off_code);
        }
}
}

/*int32_t LED_SetOut (uint32_t val) {
inti;
for (i = 0; i< LED_NUM; i++) {
if (val& (1<<i)) {
LED_On (i);
    } else {
LED_Off(i);
    }
  }
return (0);
}
*/

RESULT :

The Program for Blinking of an LED ON and OFF with Delay is interfaced with board and outputs are
verified




51
Department of Electronics and Communication Engineering
                                         20ECL67 – Embedded System Design Lab Manual   [2020 -2021] - VI Sem


Algorithm:



1) Indicate the Header File of STM32401RE

2) Start the main function

3) Declare a Variable ON and OFF and initialize to Zero

4) Call the Function LED Initialize

5) Include a Delay using FOR Loop and Set the LED to ON State

6) Include a Delay using FOR Loop and Set the LED to OFF State

7) End the Program


C) Aim: To Write a C Program for Blinking of an LED with delay.


Software Required: Keil μ Vision 5




#include"stm32F4xx_hal.h"
#include"Board_LED.h"
int main(void)
{
const unsigned intnum=0;
        unsignedinti=0;
LED_Initialize();
while(1)
{
for(i=0;i<50000:i++)
LED_On(num);
for(i=0;i<50000;i++)
        LED_Off(num);
}
}


RESULT :

The Program for Blinking of an LED ON and OFF with Delay is interfaced with board and outputs are
verified.



52
Department of Electronics and Communication Engineering
                                             20ECL67 – Embedded System Design Lab Manual   [2020 -2021] - VI Sem


Algorithm:



1) Indicate the Header File of STM32401RE.

2) Start the main function.

3) Declare a Variable ON and OFF and initialize to Zero.

4) Call the Function LED Initialize.

5) Include a Delay using FOR Loop and Set the LED to ON State.

6) Include a Delay using FOR Loop and Set the LED to OFF State.

7) End the Program.

D) Aim: To Write a C Program for Serial communication using usart0 to display a message in USART
window.

Software Required: Keil μ Vision 5

#include <stdio.h>                /* prototype declarations for I/O functions */
#include <stm32f10x.h>                /* STM32F10x definitions                */

extern void SER_Init(void);                                /* see Serial.c */

/*----------------------------------------------------------------------------
main program
 *----------------------------------------------------------------------------*/
int main (void) {               /* execution starts here                   */

SER_Init ();                  /* initialize the serial interface         */

printf ("this is akhil\n");       /* the 'printf' function call               */

while (1) {                /* An embedded program does not stop and                */
; /* ... */            /* never returns. We use an endless loop. */
 }                       /* Replace the dots (...) with your own code.*/

}


Result :
The Program for Serial communication using usart0 to display a message in USART window
is executed and observed the output in keil 5 IDE in serial window.



53
Department of Electronics and Communication Engineering
                                             20ECL67 – Embedded System Design Lab Manual   [2020 -2021] - VI Sem


Algorithm:

1) Indicate the Header File of STM32401RE

2) Start the main function

3) Call the Function Serial Initialize

4) Run a While Loop (Endless Function)

5) End the Program

E) Aim: To Write a C Program for Multiply and Accumulate among two arrays and display output in
usart window.


Software Required: Keil μ Vision 5


#include <stdio.h>          /* prototype declarations for I/O functions */
extern void SER_Init(void);                       /* see Serial.c */

/*----------------------------------------------------------------------------
  User 'strcpy' Function in In-line Assembly
 *----------------------------------------------------------------------------*/
voidmy_strcpy (char *dst, const char *src) {
intch;

  __asm {
loop: LDRB ch, [src], #1
     STRB ch, [dst], #1
     CMP ch, #0
     BNE loop
  }
}


/*----------------------------------------------------------------------------
  Multiply & Accumulate in In-line Assembly
 *----------------------------------------------------------------------------*/
#define lo64(a) (((unsigned int *)&a)[0])            /* Low 32-bits of a long long */
#define hi64(a) ((( int *)&a)[1])          /* High 32-bits of a long long */

__inline __int64 mlal (__int64 sum, int a, int b) {
  __asm{ SMLAL lo64(sum), hi64(sum), a, b }
return sum;
}

const char *txt = "Hello World!";
charbuf[16];

54
Department of Electronics and Communication Engineering
                                          20ECL67 – Embedded System Design Lab Manual   [2020 -2021] - VI Sem



int a[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
int b[10] = { 10, 9, 8, 7, 6, 5, 4, 3, 2, 1 };
__int64 sum;


Result : The Program for Multiply and Accumulate among two arrays and display output in usart window.is
executed and observe the output in keil 5 IDE in serial window.



Algorithm:



1) Indicate the Header File of STM32401RE

2) Start the main function

3) Call the Inline unction

4) Run a While Loop (Endless Function)

5) End the Program




55
Department of Electronics and Communication Engineering
                                          20ECL67 – Embedded System Design Lab Manual   [2020 -2021] - VI Sem


                                    Embedded System Design Viva Questions




Explain the different classifications of embedded systems .Give an example of each


Explain the various purposes of embedded systems in detail with illustrative examples

Differentiate between RISC and CISC processors

Explain the role of Watchdog timer in Embedded System

Explain the features of Cortex M4 processors.

Explain the advantages and applications of Cortex M4 processors

Explain the architecture of Cortex M4 processors.

Explain the memory format of Cortex M4 processors.

ARM stands for _

What are t, d, m, I stands for in ARM7TDMI.


What are the profiles for ARM architecture?

Describe the Vrious tools found in ARM Development suite.

What is the cache memory for ARM710T

Explain the Operation Modes & Privilege Levels in ARM Cortex M4

Illustrate with diagram, The Programmer’s Model for ARM Cortex M4 Processor.

Illustrate with diagram,. Memory map of cortex M4 Processor.

Number of interrupts present in Cortex-M4 processors are

What is the processor used by ARM7

How many registers are there in ARM7

What is the capability of ARM7 f instruction for a second?




56
Department of Electronics and Communication Engineering
                                         20ECL67 – Embedded System Design Lab Manual   [2020 -2021] - VI Sem




57
Department of Electronics and Communication Engineering