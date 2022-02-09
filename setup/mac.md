---
layout: home
title: Problemen Mac
nav_exclude: true
has_toc: false
---

## Problemen op de Mac?

Krijg je dan toch deze foutmelding bij uploaden van sketch, vraag dan even hulp aan de docent.
Wil je het zelf proberen op te lossen, dan staat hieronder wat (waarschijnlijk) de oplossing is...

- Open het bestand `list_ports_osx.py` als volgt via de Terminal:

```bash
# Deze plek is afhankelijk van welke versie van de Arduino IDE je hebt. 
# Kijk of je het bestand list_ports_osx.py kunt vinden en bewerken
nano ~/Library/Arduino15/packages/esp8266/hardware/esp8266/2.7.4/tools/pyserial/serial/tools/list_ports_osx.py
```

- Zet # voor deze twee regels (regels 29 en 30)

```python
#iokit = ctypes.cdll.LoadLibrary(ctypes.util.find_library('IOKit'))
#cf = ctypes.cdll.LoadLibrary(ctypes.util.find_library('CoreFoundation'))
```

- Voeg deze twee regels toe:

```python
iokit = ctypes.cdll.LoadLibrary('/System/Library/Frameworks/IOKit.framework/IOKit')
cf = ctypes.cdll.LoadLibrary('/System/Library/Frameworks/CoreFoundation.framework/CoreFoundation')
```

- Sla het bestand op met `CTRL+O` en sluit het met `CTRL+X`
- Start Arduino IDE op en probeer het opnieuw.
