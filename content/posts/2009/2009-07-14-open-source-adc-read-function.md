---
title: Open source ADC read function
author: silviu
type: post
date: 2009-07-14T16:30:43+00:00
url: /2009/07/14/open-source-adc-read-function/
categories:
  - old
tags:
  - 16f887
  - easypic5
  - microcontroller
  - mikroc
  - mikroe
  - pic
  - temp_on

---
Yes, I know, mikroC has it's own ADC library, but as always I am a sucker for open source. So I decided to write my own adc read function, so I can better understand the PIC ADC converter operation. And, in the good spirit of open source I decided to share my code. The following code is the ADC on LCD example supplied by MikroElectronika with their EasyPic5 board, and it's written in MikroC Pro. Of interest are the ADC related initializations and the **adc_read2** function. (adc_read is mikroC's own function).

Code is tested on the EasyPic5 board, but should work on other boards and / or compilers with minimal modifications. Anyways, if you were searching for an example written in C on how to read the ADC inside a pic microcontroler here it is:

```c
/*

* Based on MikroElectronika ADC on LCD example

* Uses self written ADC_Read function

*/

unsigned char ch;
unsigned int adc_rd;
char *text;
long tlong;

sbit LCD_RS at RB4_bit;
sbit LCD_EN at RB5_bit;
sbit LCD_D4 at RB0_bit;
sbit LCD_D5 at RB1_bit;
sbit LCD_D6 at RB2_bit;
sbit LCD_D7 at RB3_bit;

sbit LCD_RS_Direction at TRISB4_bit;
sbit LCD_EN_Direction at TRISB5_bit;
sbit LCD_D4_Direction at TRISB0_bit;
sbit LCD_D5_Direction at TRISB1_bit;
sbit LCD_D6_Direction at TRISB2_bit;
sbit LCD_D7_Direction at TRISB3_bit;

unsigned adc_read2(char channel)
{

switch (channel) {
case 0: {
ADCON0.CHS0 = 0;
ADCON0.CHS1 = 0;
ADCON0.CHS2 = 0;
ADCON0.CHS3 = 0;
}
case 1: {
ADCON0.CHS0 = 1;
ADCON0.CHS1 = 0;
ADCON0.CHS2 = 0;
ADCON0.CHS3 = 0;
}
case 2: {
ADCON0.CHS0 = 0;
ADCON0.CHS1 = 1;
ADCON0.CHS2 = 0;
ADCON0.CHS3 = 0;
}
case 3: {
ADCON0.CHS0 = 1;
ADCON0.CHS1 = 1;
ADCON0.CHS2 = 0;
ADCON0.CHS3 = 0;
}
case 4: {
ADCON0.CHS0 = 0;
ADCON0.CHS1 = 0;
ADCON0.CHS2 = 1;
ADCON0.CHS3 = 0;
}

}

ADCON0.GO_DONE = 1; // start conversion
while (ADCON0.GO_DONE); // wait for conversion
return (ADRESH << 8) + ADRESL; // return value
}

void main() {
INTCON = 0; // disable all interrupts
ANSEL = 0x04; // Configure AN2 pin as analog input
TRISA = 0x04;
ANSELH = 0; // Configure other AN pins as digital I/O

ADCON1.VCFG0 = 0; // set internal
ADCON1.VCFG1 = 0;
ADCON0.ADCS0 = 1; // use Vdd as reference
ADCON0.ADCS1 = 0; // use Vcc as reference
ADCON1.ADFM = 1; // result is right Justified
ADCON0.ADON = 1; // enable A/D converter

Lcd_Init();
LCD_Cmd(_LCD_CURSOR_OFF); // send command to LCD (cursor off)
LCD_Cmd(_LCD_CLEAR); // send command to LCD (clear LCD)

text = "mikroElektronika"; // assign text to string
LCD_Out(1,1,text); // print string a on LCD, 1st row, 1st column
text = "LCD example"; // assign text to string
LCD_Out(2,1,text); // print string a on LCD, 2nd row, 1st column

ADCON1 = 0x82; // configure VDD as Vref, and analog channels
TRISA = 0xFF; // designate PORTA as input
Delay_ms(2000);
text = "voltage:"; // assign text to string
while (1) {
// let's use our open source function
    adc_rd = ADC_read2(2); // get ADC value from 2nd channel
    LCD_Out(2,1,text); // print string a on LCD, 2nd row, 1st column

    tlong = (long)adc_rd * 5000; // covert adc reading to milivolts
    tlong = tlong / 1023; // 0..1023 -> 0-5000mV

    ch = tlong / 1000; // extract volts digit
    LCD_Chr(2,9,48+ch); // write ASCII digit at 2nd row, 9th column
    LCD_Chr_CP('.');

    ch = (tlong / 100) % 10; // extract 0.1 volts digit
    LCD_Chr_CP(48+ch); // write ASCII digit at cursor point

    ch = (tlong / 10) % 10; // extract 0.01 volts digit
    LCD_Chr_CP(48+ch); // write ASCII digit at cursor point

    ch = tlong % 10; // extract 0.001 volts digit
    LCD_Chr_CP(48+ch); // write ASCII digit at cursor point
    LCD_Chr_CP('V');

    Delay_ms(1);
}
}

```

Please note that I only checked for the first 4 channels in the adc_read2 function. It's easy to check for the other ADC channels using this table:

| CHS3 | CHS2 | CHS1 | CHS0 | Channel | Pin      |
|:----:|:----:|:----:|:----:|:-------:|:--------:|
|      |      |      |      |         | RA0/AN0  |
|      |      |      | 1    | 1       | RA1/AN1  |
|      |      | 1    |      | 2       | RA2/AN2  |
|      |      | 1    | 1    | 3       | RA3/AN3  |
|      | 1    |      |      | 4       | RA5/AN4  |
|      | 1    |      | 1    | 5       | RE0/AN5  |
|      | 1    | 1    |      | 6       | RE1/AN6  |
|      | 1    | 1    | 1    | 7       | RE2/AN7  |
| 1    |      |      |      | 8       | RB2/AN8  |
| 1    |      |      | 1    | 9       | RB3/AN9  |
| 1    |      | 1    |      | 10      | RB1/AN10 |
| 1    |      | 1    | 1    | 11      | RB4/AN11 |
| 1    | 1    |      |      | 12      | RB0/AN12 |
| 1    | 1    |      | 1    | 13      | RB5/AN13 |

You can find it on [GitHub][1].

 [1]: https://github.com/filviu/mikroc_bits