# Immutability
- funkce vytváření novou instanci a neupravuje už existující

špatně - měním už existující instanci todos
```
 function addTodo(todos,newTodo){
   todos.push(newTodo)
   return todos
 }
```

správně - vytvářím novou instanci
```
 function addTodo(todos,newTodo){
   return [...todos,newTodo]
 }
```

