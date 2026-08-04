## Declarative x Imperative

# Imperative
- popisuje, jak se něco má udělat, krok za krokem (cykly, podmínky, mutace stavu)

```
const doubled = []

for(let i=0;i<arr.length,i++){
 doubled.push(arr[i] * 2)
}
```


# Declarative
- nepopisuje, jak se má něco udělat ale co se má stát, bez popisu jednotlivých kroků
- detailní popis se nechá na jazyku, frameworku a nebo knihovně

```
const doubled = arr.map(arrItem => arrItem * 2)
```

- v tomto příkladu používáme metodu map, která je implementovaná imperativně (někdo napsal cyklus), ale mně jako uživateli umožňuje vyjádřit se deklarativně
- příkladem deklarativního přístupu je **function composition**

- dalším příkladem je UI v Reactu

Namísto, abychom UI elementy vytvářeli imperativně
```
const el = document.createElement("div")
el.textContent = "hello"
document.body.appendChild(el)
```

Volíme deklarativní přístup
```
function Hello(){
 return <div>hello</div>
}
```
