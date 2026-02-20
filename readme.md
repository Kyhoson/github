# Weather Station – Raspberry Pi Pico W

## Popis projektu

Tento projekt zobrazuje aktuální počasí na Grove 16x2 LCD displeji pomocí Raspberry Pi Pico W.
Zařízení automaticky zjistí aktuální geografickou polohu podle veřejné IP adresy a každých 10 minut aktualizuje data počasí pomocí OpenWeatherMap API.

Součástí projektu je synchronizace času pomocí NTP serveru a zobrazení aktuálního času na displeji.

---

## Použitý hardware

* Raspberry Pi Pico W
* Grove 16x2 RGB LCD displej (I2C)
* USB kabel
* WiFi připojení

---

## Zapojení

| LCD pin | Pico pin |
| ------- | -------- |
| VCC     | 3V3      |
| GND     | GND      |
| SDA     | GP0      |
| SCL     | GP1      |

LCD komunikuje přes I2C sběrnici.

---

## Struktura projektu

```
src/
    main.py
    wifi.py
    lcd.py
    location.py
    weather.py
    ntp_time.py
```

Konfigurační soubor:

```
config.json
```

---

## Instalace

1. Nahrajte MicroPython firmware do Raspberry Pi Pico W
2. Naklonujte repozitář:

```
git clone <URL>
```

3. Vytvořte konfigurační soubor `config.json`

```
{
  "wifi_ssid": "NAZEV_WIFI",
  "wifi_password": "HESLO",
  "openweather_api_key": "API_KLIC"
}
```

4. Nahrajte soubory do Pico pomocí Thonny nebo rshell

5. Spusťte `main.py`

---

## Funkčnost programu

Po zapnutí zařízení:

1. Na displeji se zobrazí "Connecting to WiFi"
2. Po připojení se zobrazí aktuální souřadnice
3. Následně se zobrazují informace o počasí:

* aktuální čas
* teplota
* vlhkost

Data se aktualizují každých 10 minut.

---

## Robustnost

Program obsahuje:

* automatické znovupřipojení k WiFi při výpadku
* ošetření chyb API
* NTP synchronizaci času
* oddělený konfigurační soubor

---

## Git bezpečnost

Soubor `config.json` je ignorován pomocí `.gitignore`, protože obsahuje citlivé údaje (API klíč a heslo k WiFi).

---

## Použité API

* IP geolocation API — http://ip-api.com
* OpenWeatherMap — https://openweathermap.org/api

---

## Autor

Ondřej Kýhos, Svatek Adam a Pepa Lyžmi
tgffghjhfjh
