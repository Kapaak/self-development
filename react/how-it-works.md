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
- snažit se přibližovat "state" co nejblíž ke komponentům, ktery ho potřebují (pokud mám state v parent componentu, kde ho využívá např jen 1 component z 5, tak změna toho stavu přerenderuje všech 5 komponentů a vlastně bude fungovat úplně stejně jako Context API - vyřeším presunutím state do toho 1 comp co ho potřeboval)
- namísto toho, aby 1 component obsahoval 10 dalších component je lepší to rozdělit tak, aby bylo víc component vedle sebe a ne vnořených v jednom komponentu
```
//takhle ne
function CoolFunc(){
  return(
    <div>
      <LameText/>
      ....
      <CoolFeature/>
      ....
    </div>
  )
}

//lepší řešení
function NicePage(){
  return(
    <div>
      <LameText/>
      <CoolFunc/>
      <CoolFeature/>
    </div>
  )
}
```
- pokud potřebuji zobrazit nějaký expensive component uvnitř dalšího komponentu, který se může rerenderovat, tak je dobry ho nevložit přímo do něj, ale poslat jako children, díky tomu nebude řešit rerendery toho "Design component" ale "HomePage"
```
//takhle ne
function Design(){
  return(
    <div>
      <Comp1/>
      <ExpensiveComp/>
      ....
    </div>
  )
}

//lepší řešení
function HomePage(){
  return(
    <Design>
      <ExpensiveComp/>
    </Design>
  )
}
```
