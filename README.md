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
