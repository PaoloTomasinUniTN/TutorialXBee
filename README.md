# TutorialXBee
Simple tutorial on how to connect and communicate between xbee

#
I'm following tutorial at page: https://learn.sparkfun.com/tutorials/exploring-xbees-and-xctu/all

## install fdti driver
sono i driver per il chip dentro all' xbee explorer (o all'arduino) che tramuta il segnale seriale in usb.
download and install ftdi driver from https://cdn.sparkfun.com/assets/learn_tutorials/7/4/CDM21228_Setup.exe
al termine, collegando un xbeeexplorer mediante usb, da GestioneDispositivi si vede che c'è una porta COM (es. COM3 in my case) 

## install x-ctu
questo è il software per configurare ogni xbee.
download and install X-CTU from https://www.digi.com/products/iot-platform/xctu#productsupport-utilities

vi chiederà di installare altri driver, va fatto.

## add first device

in x-ctu aggiungere il primo xbee:
1. premere sulla prima icona in alto a sinistra
1. selezionare la porta (COM3 for me)

### settings

1. channel must be the same for each device: C
1. pan ID must be the same for each device: 6599

| Setting	| Acronym	| XBee Node1	| XBee Node 2
| --- | --- | --- | --- |
| Channel	| CH | C | C | 
| PAN ID	| ID | 6599 | 6599 | 
| Destination Address High	| DH | 0 | 0 | 
| Destination Address Low	| DL | 1 | 0 | 
| 16-bit Source Address	| MY | 0 | 1 | 

## in the arduino (connected to a xbee)
if we send to the xbee the byte 0x31 (ASCII "1") it turns ON pin13
if we send to the xbee the byte 0x32 (ASCII "2") it turns OFF pin13

transfer the code to the arduino (remember to select usb in the xbee shild during transfer) 


'''
void setup() {
  // put your setup code here, to run once:

  Serial.begin(9600);

  pinMode(13,OUTPUT);
  
}

void loop() {
  // put your main code here, to run repeatedly:

  if (Serial.available() > 0) {
    unsigned char a = Serial.read();
    if (a == 0x31) {
      digitalWrite(13,HIGH);  
    }
    if (a == 0x32) {
      digitalWrite(13,LOW);  
    }
  }
}
'''

## test

using xctu send "1" to the xbee connected in USB, the xbees communicate each other and the led13 should turns ON, if you write "2" on the xctu console the led should turns off.
