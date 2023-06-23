---
title: Temperature graph on GLCD with EasyPic5
author: silviu
type: post
date: 2009-06-18T17:17:46+00:00
url: /2009/06/18/temperature-graph-on-glcd-with-easypic5/
dsq_thread_id:
  - 48858346
categories:
  - old
tags:
  - 16f887
  - ds820
  - glcd
  - ks0108
  - microcontroller
  - mikroc
  - mikroe
  - pic
  - temp_on
  - temperature

---
This is a small project I did for school. I am using the easypic 5 board from mikroelectronica to display a linegraph of the temperature read every second by the DS1820 sensor and displays it on the KS0108 based GLCD. I am using the OneWire and GLCD libraries that come with the mikroC compiler.

<figure id="attachment_279" aria-describedby="caption-attachment-279" style="width: 300px" class="wp-caption aligncenter">[![16062009023_cnv" alt="16062009023_cnv](/blog/images/2009/16062009023_cnv-300x225.jpg) ][1]<figcaption id="caption-attachment-279" class="wp-caption-text">Temperature line graph showing on the GLCD mounted on the EasyPic 5 development board</figcaption></figure>

<p style="text-align: left">
  I am using a PIC16F887 mounted on the board. You might need to adjust the code if you use a different microcontroler / development board. Also I have the DS1820 mounted in it's place with the jumper conecting it to RE2.
</p>

[cce_cpp]

// Conexiuni GLCD

char GLCD_DataPort at PORTD;

sbit GLCD_CS1 at RB0_bit;
sbit GLCD_CS2 at RB1_bit;
sbit GLCD_RS at RB2_bit;
sbit GLCD_RW at RB3_bit;
sbit GLCD_EN at RB4_bit;
sbit GLCD_RST at RB5_bit;

sbit GLCD_CS1_Direction at TRISB0_bit;
sbit GLCD_CS2_Direction at TRISB1_bit;
sbit GLCD_RS_Direction at TRISB2_bit;
sbit GLCD_RW_Direction at TRISB3_bit;
sbit GLCD_EN_Direction at TRISB4_bit;
sbit GLCD_RST_Direction at TRISB5_bit;

// Seteaza TEMP_RESOLUTION la rez. coresp. senzorului DS18x20:
// 18S20: 9 (default; poate fi 9,10,11 sau 12)
// 18B20: 12

const unsigned short TEMP_RESOLUTION = 9;

char *text = "000.0000";
unsigned temp;
char posx; // pozitia liniei de temperatura

void SetTempTextGfx(unsigned int temp2write) {
const unsigned short RES_SHIFT = TEMP_RESOLUTION - 8;
char negative,temp_whole;
unsigned int temp_fraction;

negative = 0;
// verificam daca temperatura este negativa
if (temp2write & 0x8000) {
text[0] = '-';
temp2write = ~temp2write + 1;
negative = 1;
}
// extrage temp_whole
temp_whole = temp2write >> RES_SHIFT ;
// la capatul ecranului se reia de la inceput
if (posx == 128) {
Glcd_box(4,0,128,41,0);
Glcd_box(4,43,128,64,0);
posx = 4;
}
// stergem liniile vechi
Glcd_V_line(0,41,posx,0);
Glcd_V_line(43,64,posx,0);

// desenam linia noua
if (negative == 0)
Glcd_V_line(41-temp_whole,41,posx,1);
else
Glcd_V_line(43,43+temp_whole,posx,1);
posx=posx+2;
// converteste temp_whole in text
if (temp_whole/100)
text[0] = temp_whole/100 + 48;
else
text[0] = '0';

text[1] = (temp_whole/10)%10 + 48; // Extrage cifra zecilor
text[2] = temp_whole%10 + 48; // Extrage cifra unitatilor

// extrage temp_fraction si o converteste la unsigned int
temp_fraction = temp2write << (4-RES_SHIFT);
temp_fraction &= 0x000F;
temp_fraction *= 625;

// converteste temp_fraction in caractere
text[4] = temp_fraction/1000 + 48; // Extrage cifra miilor
text[5] = (temp_fraction/100)%10 + 48; // Extrage cifra sutelor
text[6] = (temp_fraction/10)%10 + 48; // Extrage cifrazecilor
text[7] = temp_fraction%10 + 48; // Extrage cifra unitatilor

}

void main() {
short i;

ANSEL = 0; // Configureaza pinii AN ca I/O digitali
ANSELH = 0;
C1ON_bit = 0; // Dez. comp.
C2ON_bit = 0;

Glcd_Init(); // Initializeaza GLCD
Glcd_Fill(0x00); // Sterge GLCD

posx = 4;

Glcd_V_Line(0,64,3,1);
Glcd_H_Line(0,128,42,1);
for (i=0;i<64;i=i+2) Glcd_H_Line(0,3,i,1);

do {
// citirea temperaturii
Ow_Reset(&PORTE, 2); // Semnal reset Onewire
Ow_Write(&PORTE, 2, 0xCC); // Comanda SKIP_ROM
Ow_Write(&PORTE, 2, 0x44); // Comanda CONVERT_T
Delay_us(120);

Ow_Reset(&PORTE, 2);
Ow_Write(&PORTE, 2, 0xCC); // Comanda SKIP_ROM
Ow_Write(&PORTE, 2, 0xBE); // Comanda READ_SCRATCHPAD

temp = Ow_Read(&PORTE, 2);
temp = (Ow_Read(&PORTE, 2) << 8) + temp;

// Formateaza si afiseaza pe ecran

SetTempTextGfx(temp);
Glcd_Write_Text(text,80,7,1);
Delay_ms(1000);
} while (1);
}

```

You can find it on [GitHub][2] .

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/06/16062009023_cnv.jpg
 [2]: https://github.com/filviu/mikroc_bits