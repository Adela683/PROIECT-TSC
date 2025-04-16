Talevici Adela Laura 334CA

eBook Reader - Proiect TSC

Descriere genereala 
Scop: Dezvoltarea unui eBook Reader ieftin și open-source.
Software utilizat: Fusion 360 pentru proiectarea schematicii și a PCB-ului.
Ebook reader este un cititor digital inteligent, bazat pe microcontrollerul **ESP32-C6**, cu afișaj E-Ink, senzori de mediu și consum redus de energie. Proiectul oferă o experiență de citire pasivă, cu funcționalități smart și conectivitate Wi-Fi 6 pentru actualizări sau acces la rețea.

Arhitectură generală
Sistemul este centrat în jurul ESP32-C6, care coordonează toate componentele periferice:
- Ecran E-Ink pentru afișarea conținutului.
- Senzor BME688 pentru mediu.
- RTC DS3231 pentru menținerea timpului exact.
- Memorie externă SPI pentru stocare de fișiere.
- Comunicație și alimentare prin USB-C.
- Butoane fizice pentru control minimal.
- Protecții și test pad-uri pentru depanare.

Componente hardware
| Componentă | Funcție |
|-----------|---------|
| **ESP32-C6** | MCU principal – control, comunicare, Wi-Fi |
| **Ecran E-Ink 2.9"** | Afișaj monocrom SPI – ideal pentru citit |
| **BME688** | Senzor de temperatură, umiditate, presiune, calitatea aerului |
| **DS3231** | Ceas în timp real cu alarmă |
| **W25Q512 (64Mbit)** | Memorie NOR Flash SPI – stocare cărți/config |
| **MCP73831** | Circuit încărcare baterie Li-Po |
| **USB-C** | Alimentare + serial debug |
| **LDO / DC-DC** | Conversie tensiune 3.7V → 3.3V |
| **Butoane (3x)** | Reset, Boot, Funcțional (user-defined) |
| **Test Pads** | MISO, MOSI, SCK, RX, TX, 3V3, GND |

Interfețe & conectivitate
| Interfață | Componente |
|----------|------------|
| **SPI** | E-Ink, Flash externă |
| **I2C** | Senzor BME688, RTC |
| **UART** | Debug via USB-C |
| **GPIO** | Butoane, control E-Ink |

PCB Layout
- **Lățimi trasee:**
  - Putere (3V3, 5V): ≥ 0.3 mm
  - Semnal (SPI, I2C, UART): ≥ 0.15 mm

- **Decuplare VCC:**
  - 100nF pe fiecare pin de alimentare.
  - 4.7 µF – 10 µF la intrările LDO și surse principale.

- **Zonă antenă ESP32-C6:**
  - Fără cupru sub antenă – respectare layout Espressif.

- **Design Rules Check (DRC):**
  - Unghiuri ≤ 45°
  - Stitching corect GND
  - Clearance conform fabricantului

- **Componente pe Top Layer (SMD)**
- **Test pads expuse** pentru debug și programare

   Alimentare

- **USB-C (5V)** → MCP73831 → **Baterie Li-Po (3.7V)**
- **LDO 3.3V** sau DC-DC pentru alimentarea modulelor
- **Consum redus** prin folosirea modurilor de sleep (deep sleep, modem sleep)

Control și interacțiune
- **Buton RESET** → restart sistem
- **Buton BOOT** → mod programare ESP32
- **Buton USER** → acțiuni custom (ex: Next Page)


Schema Electrica 
Schema electrică a fost realizată modular, astfel încât fiecare funcție principală a dispozitivului să fie ușor de urmărit și testat. Fiecare modul este încadrat într-un bloc delimitat vizual, cu etichete clare și semnalizare a conexiunilor între blocuri.
