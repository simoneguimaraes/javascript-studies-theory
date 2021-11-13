# Conceitos do JavaScript

## Conceitos Básicos
- if, for, lógica
- Como manipular o DOM? Colocou um dado no input, como você usa esse valor no JS.
- Se clicou em um botão, como voce manipula o evento click.
- Como manipular arrays

## Como fazer sites institucionais estáticos
- Entender a semântica das tags

## JavaScript
- Formulários
- Const var let
- Hoisting
- Array - filter, map, reduce
- Funcão normal x arrow function
- Requisições com Axios - APIs públicas *Youtube: agência de viagens e Dashboard do Star Wars usando API pública

## Como fazer uma lista de tarefas
- Criar um campo de input para adicionar elementos
- Adiciona elementos no array
- Deleta itens do array
- Reordenar o array
- Como marcar quais tarefas voce ja fez

## JS é uma linguagem orientada a objetos

- O JS é um sistema de tipos - tipos primitivos e complexos
- O JS nao é fortemente tipada - podemos declarar uma variável sem especificar o tipo de valor. E o tipo pode mudar.

```Existem os dados de tipo primitivo (number, string, boolean, undefined, null, symbol). O restante é Objeto (Arrays, funções, objetos, regex).```

```O que muda entre esses tipos de dados é que **os dados de tipo primitivo são declarados como valor** e **os objetos são passados como referência**.```

## Imutabilidade nos Tipos de Dados

- A mutabilidade e a imutabilidade estão relacionados ao fato de que, quando você copia o dado, ele altera ou não o seu original.
- Quando você faz uma cópia de dados primitivos, o original nunca muda.
- Quando você faz uma cópia de dados do tipo objeto, o original é alterado.

### Dados do tipo primitivo
Os dados de **tipo primitivo** são passados por **valor** e são **imutáveis**:
```
let name = 'Carlos'
let firstName = name
```

- Quando voce cria as duas variáveis de tipo primitivo, é criado um ponto de memória específico pra ele.
- Então se eu alterar name, firstName não é alterado. 
Se eu fizer:
```
let fullName = 'Simone Guimaraes'
let firstName = fullName.slice(0, 6)
console.log(firstName) // 'Simone'
```
A variável fullName não será alterada.

### Dados do tipo Objeto
Os dados que são do **tipo Objeto** são passados por **referência** e são **mutáveis**:
```
let name = {}
let firstName = name
```

- Quando voce cria a variável de tipo objeto 'name', é criado um ponto de memória específico pra ele. Porém, quando voce cria a variável 'firstName' que tem como referência o 'name', não é criado outro espaço de memória para ele. 
- Os dois vão apontar para *o mesmo espaço na memória*.
- Então se eu alterar name, firstName é alterado e vice-versa. 
Se eu fizer:
```
let numbers = [4, 3, 2, 1]
let orderedNumbers = numbers.sort()
console.log(numbers) // [1, 2, 3, 4]
```
A variável numbers foi alterada, sofreu uma mutação.


## Tópicos
Como usar as tags HTML certas
CSS rápido - reaproveitamento de classes, usar flexbox, fazer responsividade
Saber os principais métodos - map, filter, reduce
Diferença entre as variáveis const, let e var
O que é Hoisting, Escopo, Arrow Function
O que significa Linguagem Orientada a Objetos
https://github.com/isadorastan/estudos

### Hoisting

- JavaScript's interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.
- One of the advantages of hoisting is that it **lets you use a function before you declare it in your code**. 
- Hoisting works with variables too, so you can use a variable in code before it is declared and/or initialized. 
- However JavaScript only hoists declarations, not initializations! This means that initialization doesn't happen until the associated line of code is executed, even if the variable was originally initialized then declared, or declared and initialized in the same line.

### Escopo
#### Variável em escopo global:
- De dentro da funcao, voce consegue acessar as variaveis de escopo global
```
let name = 'Joao'
{
console.log(name) // 'João'
}
```

#### Variável em escopo de função:
- Você consegue não consegue acessar fora do escopo da função
```
{
let name = 'Joao'
}
console.log(name) // undefined
```

### Nested Scope
- Voce consegue ver as coisas que estão no escopo mais para fora, mas não consegue ver em um escopo para dentro.
```
let name = 'pedro'
{
  let name = 'jose'
  {
    let name = 'maria'
  }
}
```

### Closure
No JS, a funcao vai buscar o valor mais recente da variavel para executar.
```
let name = 'lucas'

function print() {
  console.log(name)
}

name = 'paula'

print() // 'paula'  
```
Ao inves de ter uma variável, a closure acontece com uma funcao dentro de outra:
```
function print(variable) {
  return function func(otherVariable) {
    console.log(variable)
    console.log(otherVariable)
  }
}
let a = print('jose')
a('maria')
```
### Arrow Function
Difference between an arrow function and a normal function
() => {}

### Explicit Type Coersion
Quando voce quer fazer a mudança de tipo da variavel
```
let a = '1'

console.log(a)                  // string
console.log(typeof parseInt(a)) // number
```
```
let a = 1.34                      // number
console.log(typeof a.toString())  // string
```

### Implicit Type Coersion
- Quando o JS faz a conversao quando voce usa '+', '==' para conseguir executar a ação.
- Para evitar isso, usar o "===" para não haver erros.
- Voce pode usar o "==" para checar dados com 'null' e 'undefined'.
```
let a = 1
const b = 'Hello'

console.log(b + a) // 'Hello1'
```

### NaN
Quando voce recebe o erro de "NaN", o JS está sinalizando que não é um número. 
Para checar se algo é NaN:
```
const a = parseInt('loops')
console.log(isNaN(a)) // true
```

### Array

- É uma variável que consegue armazenar uma lista de dados.
```
const a = [1, 2, 3. 4. 5]

console.log(a) // (5) [1, 2, 3. 4. 5]
```
Para acessar um elemento da array, voce busca pelo [índice]:
```
console.log(a[0])
```
- Para adicionar um elemento na array:
- Push adiciona um elemento ao final
```
a.push(6)
```
Em arrays, voce pode misturar os tipos de dados:
```
const arr = [1, 'mae', '56']
```
Voce pode adicionar uma array a uma array:
```
a.push([7, 8, 9])
```
Como pegar o tamanho da array
```
a.length
```
Como pegar o último elemento da array
```
console.log(a.length - 1)
```
Como pegar o elemento no meio da array: 
```
const alph = ['a', 'b', 'c', 'd', 'e']
console.log(alph[Math.floor(alph.length/2)])
```
### Nested Array
Como acessar os índices quando há array dentro de array
```
const a = [
  [10, 11, 12],
  ['hi', 'bye']
]

console.log(a[1][0]) // 'hi'
``` 
Como imprimir os números 4, 8 e 11
```
const a = [
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10],
  [11, 12, 13, 14, 15]
]
console.log(a[0][3], a[1][2], a[2][0])
```

### Objects


