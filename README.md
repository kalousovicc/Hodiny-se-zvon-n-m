# 🔔 Školní hodiny se zvoněním (Raspberry Pi Pico)

Maturitní projekt realizující plně funkční školní hodiny s automatickým zvoněním na platformě **Waveshare Pico-Clock-Green** a **Raspberry Pi Pico**.

- **Škola:** Střední průmyslová škola elektrotechniky a informačních technologií, Dobruška
- **Školní rok:** 2026/2027
- **Obor:** 18-20-M/01 Informační technologie (ŠVP Počítačové sítě a programování)
- **Vedoucí práce:** Ing. Jiří Vintera

---

## 🎯 Cíle a funkce projektu

### Povinný základ (MVP)
- **Konfigurace přes JSON:** Časy zvonění jsou uloženy externě v souboru `schedule.json` přímo ve flash paměti zařízení. 
- **Manuální vypnutí (Mute):** Stiskem tlačítka se zvonění pro zbytek aktuálního dne vypne a o půlnoci se automaticky opět aktivuje.
- **Konstrukce a ekonomika:** Fyzické uchycení (stojánek / nástěnný držák) s přístupem k USB portu, kusovník (BOM) s reálnými cenami a kalkulace odpracovaného času.

## Hlavní funkce
- **Zobrazení času:** Aktuální čas ve formátu `HH:MM` a zkratka dne v týdnu (`Po`, `Út`, `St`, `Čt`, `Pá`, `So`, `Ne`) na LED maticovém displeji.
- Udržování přesného času pomocí integrovaného obvodu se záložní baterií.
- Odlišné zvuky pro **začátek hodiny** a **začátek přestávky**.
- Manuální dočasné vypnutí zvonění na aktuální den stiskem tlačítka s vizuální indikací a automatickou reaktivací o půlnoci.
- *(Volitelné rozšíření)* Synchronizace času přes NTP a správa přes Home Assistant (Pico W).

## Použitý hardware a software
- **Mikrokontrolér:** Raspberry Pi Pico / Raspberry Pi Pico W
- **Displej a periferie:** Waveshare Pico-Clock-Green 
- **Jazyk a prostředí:** MicroPython, Thonny IDE / VS Code
- ## 🛠️ Hardware a nákupní seznam (BOM)

### Co už je k dispozici
- **Waveshare Pico-Clock-Green** (obsahuje LED matici, přesný RTC čip DS3231, integrovaný piezo bzučák a 3 boční tlačítka)
- **Raspberry Pi Pico** (mikrokontrolér)
- **Datový Micro-USB kabel** | Programování a úprava `schedule.json` | Musí podporovat přenos dat (ne pouze nabíjení)
- **Napájecí adaptér 5V USB** | Trvalé napájení ze zásuvky | Běžný 5V adaptér 

### Co je potřeba dokoupit / zajistit
| **Baterie CR1220 (3V)** | Záloha RTC čipu při výpadku proudu | Knoflíková baterie do slotu na zadní straně desky |
| **Pinové lišty (Headery)** | Propojení Pica s deskou hodin | Pouze pokud je Pico nemá připájené z výroby |
| *Externí bzučák (volitelné)* | Hlasitější zvuková signalizace | Aktivní bzučák 3.3V/5V nebo piezo měnič |
| *Externí tlačítko (volitelné)* | Pohodlnější ovládání mimo krabičku | Panelový mikrospínač + Dupont vodiče |
| *Materiál na kryt (volitelné)* | Mechanické uchycení | Filament PETG (3D tisk), překližka nebo plexisklo |
| *Raspberry Pi Pico W (volitelné)* | Rozšíření o Wi-Fi (NTP + Home Assistant) | Pouze v případě realizace síťových funkcí |

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







