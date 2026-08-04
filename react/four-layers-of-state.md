# Four layers of state
Jaké typy stavů rozeznáváme

## Layer 1 (Server state)
- zde se uchovávají data, která nevlastní FE (jde o stav na BE a DB)
- potřebuje cachování, refetching, invalidaci a loading state

## Layer 2 (Global state)
- stav, který je sdílený napříč komponenty (patří čistě FE)
- například Zustand, Context API

## Layer 3 (Local state)
- stav, který patří komponentě a nikoho jiného to nezajímá
- například jestli je dropdown otevřený / zavřený

## Layer 4 (URL state)
- stav uložený v URL, path params, query params
- například stránkování
- stav je sdílený napříč zařízeními a uživateli, přežije refresh stránky
- zdroj pravdy je query, ne state
