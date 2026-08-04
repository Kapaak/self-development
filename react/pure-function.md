# Pure Function
- vrací vždy pro stejný vstup stejný výstup
- nemá žádný side effect (nevolá API ani nevkládá nic do DB)
- pure funkce dělají kód čistější, protože debugování je na první pohled jasné a neřeším nějaké proměnné, které by mohly měnit stav funkce

Tohle není pure function, protože hodnota counteru na výstupu nebude vždy stejná pro daný vstup.
```
let counter = 0;

  function increment(){
    counter += 1

    return counter
  }
```

Tohle je pure funkce
```
const increment = counter => counter+1
```
