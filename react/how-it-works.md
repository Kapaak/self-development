# React
Bližší info k tomu, jak React funguje - proč dělá, co dělá 😀

## JSX
- syntaxe pro psaní HTML uvnitř JS souborů
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
- snažit se přibližovat "state" co nejblíž ke komponentům, ktery ho potřebují, pokud mám state v parent componentu, kde ho využívá např jen 1 component z 5, tak změna toho stavu přerenderuje všech 5 komponentů ikdyž ho nevyužívají
  - vlastně pak bude fungovat úplně stejně jako Context API
  - vyřeším presunutím state do toho 1 comp co ho potřeboval, nebo ty komponenty, ktere se nemají měnit obalit v memo() - což není úplne 10/10 řešení, protože pak se musí v tom comp řešit porovnání mezi předchozím stavem
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
- proč context vytváří rerendery, ikdyž použiju memo na komponenty? Protože když dám <MyContext.Provider value={{items,setItems}}/> tak items a setItems jsou součástí nového objektu, který se pokaždý mění, protože objekty jsou passed by reference
  - vyřeší se to tak, že vytvoříme 2 Contexty a obalíme nejdřív ten který ponese hodnotu která se nemění contextem, který se bude měnit (používá se tu useReducer, protože dispatch i setState když se passnou tak se nemění, ale dispatch jde použít pro víc situací)
  - ![image](https://github.com/Kapaak/self-development/assets/58420887/90754dd0-2b0b-4ce9-a87d-74641a97b699)
  - pak se na to může např vytvořit takový hook, který zakryje používání useContext()
  - ![image](https://github.com/Kapaak/self-development/assets/58420887/e2d57fe5-ac64-43f4-854b-b92b15173a79)
  - pokud chceme posílat další hodnotu, je potřeba vytvořit další Context a obalit to :(



