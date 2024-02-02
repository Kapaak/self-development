# React
Bližší info k tomu, jak React funguje - proč dělá, co dělá 😀

## JSX
- syntaxe pro psaní HTML uvnitř JS filů
- JSX se transformuje do JS kódu ještě předtím, než se zobrazí v browseru
- tuto transformaci dělá tzv. transpiler - Babel, který transformuje JSX kód do série function callů


```
//před transformací
const element = <h1>Hello, world!</h1>;

//po transformaci
const element = React.createElement("h1", null, "Hello, world!");
```
pro transformaci funkce se navíc do createElement přidá {}
```
//před transformací
function Greet() {
  return <h1>Hello World!</h1>;
}

// po transformaci
function Greet() {
  return React.createElement("h1", {}, "Hello, World!")
}
```

- v React verzi 17 přibyla nová JSX transform feature, která umožňuje používání JSX syntaxe bez nutnosti importu Reactu na začátku filu

```
// Inserted by a compiler (don't import it yourself!)
import {jsx as _jsx} from 'react/jsx-runtime';
```


## Fiber

## Rendering

## Prevent rerenders
