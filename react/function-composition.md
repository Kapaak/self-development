# Function composition
- používá se, když například chci vyřešit nějakou složitější operaci, která se dá rozdělit na více funkcí
- vstup jedné funkce je získává další funkci, která může získávat další funkci.

Příkladem je níže definovaná funkce slugify.
```
const normalize = str => str.trim().toLowerCase()
const removeSpaces = str =>str.replace..
const limitLength => str => str.slice(0,20)

const slugify = str => limitLength(removeSpaces(normalize(str)))
```
