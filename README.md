
# Školní hodiny se zvoněním (Waveshare Pico-Clock-Green)

Maturitní projekt zaměřený na realizaci digitálních školních hodin s automatickým zvoněním na platformě **Raspberry Pi Pico** a LED maticového modulu **Waveshare Pico-Clock-Green**.

## Hlavní funkce
- Zobrazení aktuálního času (`HH:MM`) a zkratky dne v týdnu (`Po`–`Ne`) na zeleném LED displeji.
- Udržování přesného času pomocí integrovaného obvodu se záložní baterií.
- Odlišné zvuky pro **začátek hodiny** a **začátek přestávky**.
- Manuální dočasné vypnutí zvonění na aktuální den stiskem tlačítka s vizuální indikací a automatickou reaktivací o půlnoci.
- *(Volitelné rozšíření)* Synchronizace času přes NTP a správa přes Home Assistant (Pico W).

## Použitý hardware a software
- **Mikrokontrolér:** Raspberry Pi Pico / Raspberry Pi Pico W
- **Displej a periferie:** Waveshare Pico-Clock-Green 
- **Jazyk a prostředí:** MicroPython, Thonny IDE / VS Code

## Struktura repozitáře
- `/firmware` – zdrojové kódy v jazyce MicroPython (`main.py`, knihovny displeje a RTC)
- `/config` – vzorový konfigurační soubor `schedule.json`
- `/docs` – osnova a text maturitní práce, schémata zapojení, fotodokumentace
- `/cad` – podklady pro mechanické uchycení / 3D tisk krytu
