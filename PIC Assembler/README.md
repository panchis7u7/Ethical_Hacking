# PIC Assembler Concepts (PIC-as)
## TIMER 0.
Functions as:
+ Timer. (If the Oscillator [Fosc / 4] is used for counting)
+ Counter. (If the external T0CKI pin is used)

It depends on the following registers for configurations:
<b>OPTION_REG</b>
    - <b>T0SE</b>: Timer0 Source Edge Select bit; 0 = high to low, 1 = low to high.
    - <b>T0CS</b>: Timer0 Clock Source Select bit (Fosc or T0CKI).
    - <b>PSA</b>: Prescaler Assignment bit. 0 = Assignes the PSC to the Timer0.
    - <b>PS<2:0></B>: Prescaler Rate Select bits:e

| Bit Value |  Timer0 Rate  |  WDT Rate |
|-----------|---------------|-----------|
|    000    |      1:2      |    1:1    |
|    001    |      1:4      |    1:2    |
|    010    |      1:8      |    1:4    |
|    011    |      1:16     |    1:8    |
|    100    |      1:32     |    1:16   |
|    101    |      1:64     |    1:32   |
|    110    |      1:128    |    1:64   |
|    111    |      1:256    |    1:128  |

<b>INTCON</b>
    - <b>TMR0IF</b>: TMR0 Overflow Interrupt Flag Bit. 1 = Overflowed.

#### TIMER0 as a Counter.

$TMR0 =256-\frac{Xc}{pre}$

Where: 
TMR0 is a value between 0 and 255.
Xc = Value of the count.
Pre = Values of the prescaler.

#### TIMER0 as a Timer.

$TMR0 =256-(\frac{Xt}{(\frac{4}{f})pre})$

Where: 
TMR0 is a value between 0 and 255.
Xt = Value of time in ms.
Pre = Values of the prescaler.
F = Frecuency of oscillation in Hz.