# EbookReader
OpenBook eBook Reader

Dispozitivul e-book se bazeaza pe un microcontroller ESP32-C6 si include un afisaj E-Paper.

[Diagrama Bloc](Images/diagram.png)

`Diagrama bloc afiseaza componente:`
- ESP32-C6 (unitate centrala)
- Afisaj E-Paper
- Cititor SD card
- RTC DS3231
- Senzor ambiental BME688
- Control incarcare baterie Li-Po
- Modul flash extern 64MB
- Interfata USB-C
- Circuit de reglare tensiune (LDO)

### BOM - Bill Of Materials

[Fisier BOM](Manufacturing/BOM.csv)
https://ro.mouser.com/
https://www.comet.srl.ro/


Alimentare
- Alimentare principala prin USB-C.
- Reglator de tensiune LDO (IC4 - XC6204A33) pentru conversia de la 5V la 3.3V.
  
Microcontroller
- ESP32-C6 = unitatea principala ce controleaza restul pieselor.
- Se ocupa cu gestionarea interfetei cu utilizatorul, afisajul EPD, comunicatia cu SD card-ul, RTC si senzorul ambiental.
  
Stocare
- Slot microSD pentru stocare.
- Memorie flash externa W25Q512JVSIQ conectata prin SPI pentru firmware suplimentar sau caching.


### Alocarea pinilor ESP32-C6

| Functie                | Pin ESP32-C6         | Observatii |
|------------------------|----------------------|-------------|
| SD Card                | IO2, IO3, IO4, IO5   | SPI |
| E-Paper Display        | IO8, IO9, IO10       | SPI |
| Senzor BME688          | IO6 (SCL), IO7 (SDA) | I2C |
| RTC DS3231             | IO6 (SCL), IO7 (SDA) | I2C shared |
| Flash extern SPI       | IO0, IO1, IO2        | SPI |
| Boot Button            | IO9                  | Reset GPIO |
| Buton IO               | IO10                 | Control interfata |
| UART Debug             | IO20 (TX), IO21 (RX) | Conexiune seriala |
| Ecran Type Select      | IO18, IO19           | Selectare tip e-paper |

Bugs: La piesa SAMACSYS_PARTS_USB4110GFA erori de tip `Smd-hole` la partea de rutare a pcb ului.
  
La directorul images din proiect sunt imagini cu schematic ul, pcb si 3d.
