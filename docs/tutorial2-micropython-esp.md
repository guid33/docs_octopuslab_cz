# ![logo](img/logo_small.png) Tutorial 2

V předchozím [tutorial 1](/tutorial1-python) jsme se seznámili s úplnými základy. V tomto druhém pokračování už budeme potřebovat ESP32. Předpokládáme, že již máte na svém ESP [nainstalovaný Micropython](/install).

---
## ESP32 - DoIt nebo ESP32board

### Rozsvítíme LED diodu?

Na velké části ESP modulů máme k dispozici vestavěnou svítivou diodu na PINU 2. Nejjednodušší, jak nastavit hodnotu `value()` na pinu `Pin` je následující způsob:

```python
>>> from machine import Pin
>>> led = Pin(2, Pin.OUT)
>>> led.value(1)
```

### Teplota u procesoru
```python
>>> import esp32
>>> esp32.raw_temperature()
127
```

### Hallova sonda - magnetického pole
```python
>>> import esp32
>>> esp32.hall_sensor()
129 # cca standard hodnota
```

```python
>>> esp32.hall_sensor() 
976 # po přiložení magnetu 
```

### Piezzo

Pro další pokus je vhodné mít už kromě modulu i nějakou možnost připojid další LED diodu nebo například malý piezzo "pípák":

![breadboard](https://www.octopuslab.cz/wp-content/uploads/2019/08/Sn%C3%ADmek-obrazovky-22-768x525.png)

```python
from components.buzzer import Buzzer
piezzo = Buzzer(18)
piezzo.beep()
 
# napřímo přes octopus():
beep()                   
# základní pípnutí (1000,50) > 1kHz na 50ms

beep(440,500)            
# komorní a 440Hz na 0.5s 

>>> from components.buzzer import notes 
>>> Notes.A4                
440    
#k dispozici jsou tóny C3-C7 
>>> buzzer.play_tone(Notes.A4)   # = tone(440) 
```

## Víceřádkové programy - funkce, podmínky a cykly

*Opakování a shrnutí.*

### Obyčejná sekvence příkazů

Zatím jsme používali terminál a většinou nám stačil jeden příkaz nebo postupná sekvence příkazů na několika málo řádcích: 

```python
>>> from machine import Pin
>>> led = Pin(2, Pin.OUT)
>>> led.value(1)
```

Už jsem se o tom zmínili několikrát a už byste to mohli mít i zažité. Po odeslání (ENTRem) mikrokontrolér příkazy na řádku vykoná 
a opět nám oznámí své *další očekávání pro nové pokyny* promptem `>>>`.
Končí-li však řádek dvojtečkou `:`, Python to vyhodnotí jako "blok" a vyzve nás pro pokračování třemi tečkami `...`:

### Definování vlastní funkce - def

Vlastní funkce je "podprogram", který se využívá pro opakující se bloky kódu nebo pro zpřehlednění rozsáhlejších programů.
Podle příkazu  `def ` a dvojtečky `: ` na konci řádku pozná Python, že uživatel definuje svou vlastní funkci, třeba pro součet dvou vstupních čísel:

```python
>>> def suma(x, y):
... return x + y

>>> suma (1, 2)
3
```

### Podmínka
**Program** - to ale není jen obyčejná posloupnost příkazů. Často se používá *podmíněné větvení* - což znamená, že na základě vyhodnocení nějakého výrazu se program může chovat různým způsobem a může i pokračovat různým "směrem".
Opět se používá stejná konstrukce s dvojtečkou za výrazem podmínky `if`:
```python
>>> cislo = 10
>>> if cislo<0:
... print("cislo je zaporne")
...
>>>
```

### Cyklus while nebo for

Dvojtečka je i ve `while` cyklu:

```python
>>> cislo = 0
>>> while cislo<2:
... print(cislo)
... cislo = cislo +1
...
0
1
2
>>>
```

Podobně pak i `for` cyklus:
```python
>>> for cislo in range(6):
... print(cislo, end="")
...
012345>>>
```



---