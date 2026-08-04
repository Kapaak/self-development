# Currying x Partial application

## Currying
- použije se když mám nějakou funkci, která na vstupu získává více parametrů.
- tuto funkci zjednodušíme tak, že vytvoříme currying funkci, která na vstupu ziská právě jeden parametr a na výstupu volá další funkci, která volá také právě jeden parametr
- poslední takto zřetězená funkce zpracovává výsledek

## Partial application
- mám funkci, která na vstupu získává více parametrů achci pro nějakou situaci některé z nich předvyplnit
- proto vytvořím novou funkci z této stávající funkce a předvyplním nějaké ze vstupů a tím je jakoby uzamknu a dovolím vkládat jen ty, které jsou potřeba
- vytvořím si obecnou funkci tím, že část jejich argumentů "natvrdo" předvyplním
- klasickým příkladem je .bind
