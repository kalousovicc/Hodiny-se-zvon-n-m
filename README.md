
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

```py

{
  "zvoneni_povoleno": true,
  "povolene_dny": {
    "Po": true,
    "Ut": true,
    "St": true,
    "Ct": true,
    "Pa": true,
    "So": false,
    "Ne": false
  },
  "zvukove_vzory": {
    "hodina": {
      "frekvence_hz": 2000,
      "delka_impulzu_ms": 1500,
      "pocet_opakovani": 1,
      "pauza_ms": 0
    },
    "prestavka": {
      "frekvence_hz": 2500,
      "delka_impulzu_ms": 400,
      "pocet_opakovani": 3,
      "pauza_ms": 250
    }
  },
  "rozvrh": [
    { "cas": "07:45", "typ": "hodina",     },
    { "cas": "08:30", "typ": "prestavka",  },
    { "cas": "08:35", "typ": "hodina",    },
    { "cas": "09:20", "typ": "prestavka", },
    { "cas": "09:25", "typ": "hodina",     },
    { "cas": "10:10", "typ": "prestavka",  },
    { "cas": "10:30", "typ": "hodina",     },
    { "cas": "11:15", "typ": "prestavka",  },
    { "cas": "11:25", "typ": "hodina",     },
    { "cas": "12:10", "typ": "prestavka", }
     { "cas": "12:20", "typ": "hodina", }
   { "cas": "13:05", "typ": "prestavka", }
  ]
}
```
