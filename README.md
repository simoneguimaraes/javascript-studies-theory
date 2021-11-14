# Conceitos do JavaScript

## Conceitos Básicos
- if, for, lógica
- Como manipular o DOM? Colocou um dado no input, como você usa esse valor no JS.
- Se clicou em um botão, como voce manipula o evento click.
- Como manipular arrays - saber os principais métodos (map, filter, reduce)
- Diferença entre as variáveis const, let e var
- O que é Hoisting, Escopo, Arrow Function
- O que significa Linguagem Orientada a Objetos

### Como fazer sites institucionais estáticos
- Entender a semântica das tags
- Como usar as tags HTML certas
- CSS rápido - reaproveitamento de classes, usar flexbox, fazer responsividade

### JavaScript
- Formulários
- Const var let
- Hoisting
- Array - filter, map, reduce
- Funcão normal x arrow function
- Requisições com Axios - APIs públicas *Youtube: agência de viagens e Dashboard do Star Wars usando API pública

### Como fazer uma lista de tarefas
- Criar um campo de input para adicionar elementos
- Adiciona elementos no array
- Deleta itens do array
- Reordenar o array
- Como marcar quais tarefas voce ja fez

### Hoisting
- JavaScript's interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.
- One of the advantages of hoisting is that it **lets you use a function before you declare it in your code**. 
- Hoisting works with variables too, so you can use a variable in code before it is declared and/or initialized. 
- However JavaScript only hoists declarations, not initializations! This means that initialization doesn't happen until the associated line of code is executed, even if the variable was originally initialized then declared, or declared and initialized in the same line.

### Return
A função é executada até a parte do 'return'. Tudo que vem em seguida não é executado. Nesse caso, a função nao executa o console.log. 
```
function sayHi(name) {
  return `Hello ${name}`
  console.log(`Say bye`)
}
```
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

É uma variável que consegue armazenar uma lista de dados.
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
Coleção de informação organizada por nome e valor.
```
let person = { key : value }
```
```
let person = {
  name: 'Simone',
  age: 27,
  favoriteFood = 'Pizza'  
}
```
Para acessar as propriedades desse objeto, é só usar o '.':
```
console.log(person.age)
```
Voce tambem pode ter uma funcao dentro do objeto:
```
let car = {
  make: 'volks',
  model: 'black 2009',
  isUsed: true,
  makeNoise: function() {
    console.log('Vroom')
  },
  sayBye() {
    console.log('Bye')
  }
}


car.makeNoise()
console.log(car.make)
console.log(car.isUsed)
```

### Nested Objects and Arrays
- Para acessar as propriedades de um objeto, usar o '.'. 
- Para acessar as propriedades do array, usar o [índice].

```
let person = {
  name: 'Simone',
  age: 27,
  hobbies: ['Travelling', 'Photography'],
  address: {
    street: 'Rua Jose Bonifacio',
    city: 'Lima'
  }
}

console.log(person.address.city)
console.log(person.hobbies[1])
```
Como mudar a propriedade de um objeto:
```
let book = {
  title: 'O pequeno Rei',
  author: {
    name: 'Jose Bonifacio',
    age: 73
  genre: ['Mistery', 'Adult'],
  }
}

book.author.age = 87
console.log(book.author.age)
```

### Referência x Valor
#### Os tipos primitivos possuem um valor.
- Nesse caso, o valor de c será o valor de a + 1.
```
let a = 10
let b = 2
let c = a + 1
```
#### Os tipos Objeto possuem uma referência - um espaço de memória alocado a eles
É importante saber que **o valor de um objeto é o seu endereco de memoria** 
```
let a = [1, 2]
let b = a

a = <0x01> = [1, 2]
b = <0x01> = [1, 2]
```
- O endereço de memória de 'a' e 'b' é o mesmo '<0x01>' e o valor é [1, 2].
- Caso voce altere o valor de b, as duas variaveis vao mudar de valor.
```
let a = [1, 2]
let b = a
b.push(3)

a = <0x01> = [1, 2, 3]
b = <0x01> = [1, 2, 3]
```
Quando voce cria duas arrays com o mesmo nome, elas terão diferentes espaços de memoria
```
let a = [1, 2]  //<0x01>
let b = [1, 2]  //<0x02>
console.log(a === b) // false
```
- O valor de um objeto é o seu endereço de memoria. Então quando voce declara ele com const, o que vai ficar imutavel é o seu endereco de memoria.
- Por isso que é possível alterar o conteúdo de um objeto mesmo declarando ele com const.
```
const c = [1, 2, 3]
c.push(6)
```
- Para mudar um espaço de memória, voce precisa redefinir o objeto
- Se usar o const nesse caso, vai dar erro
```
let a = [1, 2]  //<0x01>
let b = [1, 2]  //<0x02>
a = [1, 2, 3]   //<0x03>
```

```
const a = [1, 2]
const elementoToAdd = 3

add(a, elementoToAdd)

function add(array, element) {
  array.push(element)
}
```

## Array Methods
### 1 - forEach
- Fazer um loop por todos os elementos
- A funcao vai ser executada uma vez para cada elemento da array
- Ele nao retorna nada, voce nao consegue guardar esse valor

```
const a = [1, 2, 3, 4, 5]
a.forEach((currentNumber) => console.log(currentNumber))
```
```
const a = [1, 2, 3, 4, 5]
a.forEach((currentNumber, index) => console.log(`${index}: ${currentNumber}`))
```

### 2 - map
- Ele percorre todos os elementos da array e faz uma mesma modificação em cada um
- Você cria uma nova array com uma modificação em todos os elementos
- A diferença é que ele retorna um valor na função - que pode ser guardado em uma variável
- Ele nao modifica a array original

```
const a = [1, 2, 3, 4, 5]

const dubleNum = a.map((currentNumber) => {
  return currentNumber * 2 
})

console.log(dubleNum) 
// [2,4,6,8,10]
```

### 3 - filter
- Ele percorre todos os elementos da array e retorna apenas os elementos os que dão 'true' na condição que voce criou
- Voce retorna uma array menor com apenas os valores que voce quer
- Se o valor retornar 'true' ele mantém na array. Se retornar 'false' ele retira da array
- Você cria uma nova array
- Ele nao modifica a array original

```
const a = [1, 2, 3, 4, 5]

const lessThanThree = a.filter((currentNumber) => {
  return currentNumber <= 2 
})

console.log(lessThanThree) 
// [1, 2]
```

### 4 - find
- Ele percorre todos os elementos da array e retorna o primeiro elemento que der 'true' na condição que voce criou
- Ele retorna apenas o valor
- Ele nao modifica a array original

```
const a = [1, 2, 3, 4, 5]

const biggerThanTwo = a.find((currentNumber) => {
  return currentNumber > 2 
})

console.log(biggerThanTwo)
// 3
```
### 5 - some
- Ele percorre todos os elementos da array e verifica se pelo menos um elemento dá 'true' na condição que voce criou
- Ele retorna apenas true/false indicando se existe algum elemento com essa condição
- Ele nao modifica a array original
```
const a = [1, 2, 3, 4, 5]

const isTrue = a.some((currentNumber) => {
  return currentNumber > 2 
})

console.log(isTrue)
// true
```

### 6 - every
- Ele percorre todos os elementos da array e verifica se todos os elementos dão 'true' na condição que voce criou
- Ele retorna apenas true/false indicando se existe todos os elementos tem essa condição
- Ele nao modifica a array original
```
const a = [1, 2, 3, 4, 5]

const isTrue = a.every((currentNumber) => {
  return currentNumber > 3
})

console.log(isTrue)
// false
```
### 7 - reduce
- Ele pega todos os elementos da array e reduz a apenas um valor, por meio de um loop por todos os elementos e fazendo algo a cada vez.
- Ele usa pelo menos dois parâmetros
- Ele retorna um valor
- O primeiro parametro é o 'acumulador'
- O segundo parâmetro é o 'inicializador' (0). Esse 'zero' no final da funcao simboliza o valor do primeiro parametro da funcao reduce (sum) quando a funcao iniciar. 
- Ele nao modifica a array original
```
const a = [1, 2, 3, 4, 5]

const sumNumbers = a.reduce((sum, currentNumber) => {
  return sum + currentNumber
}, 0)

// 0 + 1 = 1
// 1 + 2 = 3
// 3 + 3 = 6
// 6 + 4 = 10
// 10 + 5 = 15

console.log(sumNumbers)
// 15
```
Outro exemplo:
```
const items = [
  { price: 10, isAvailable: true }, 
  { price: 20, isAvailable: true }, 
  { price: 14, isAvailable: true }, 
  { price: 1, isAvailable: true }, 
  { price: 6, isAvailable: true }
]

const totalPrice = items.reduce((sum, currentItem) => {
  return sum + currentItem.price
}, 0)

console.log(totalPrice)
// 51
```
### 8 - includes
- Voce passa um valor e ele checa se o valor existe na sua array
- Ele retorna true or false
```
const a = [1, 2, 3, 4, 5]

const isTrue = a.includes(2) 

console.log(isTrue)
// true
```

## String Template Literals
- Voce pode combinar strings com variáveis
```
let name = 'Simone'
console.log(`Hello ${name}`)
```
## Constructor
### New
Voce pode usar a palavra-chave New para criar um objeto:
```
const date = new Date()  --> vai mostrar a data atual '21-11-14' como um objeto
console.log(date)
console.log(date.getDay()) // 0 (domingo)
```

### this
Ao inves de criar uma funcao para gerar novos objetos (um novo usuário do site com suas propriedades, por exemplo), como essa:
```
function createUser(name, age) {
  return { name: name, age: age, isHuman: true }
}

const user = createUser('Simone', 27)
```
- Voce pode usar a palavra-chave 'this' para na função Constructor:
- Constructor function --> constructs a new object of a specified type
- this -> keyword - referrences the current object you are trying to create
- O que acontece no Constructor: quando voce usa a palavra-chave 'this', ele cria um novo objeto vazio 'this = {}' e retorna esse objeto no final da funcao 'return this'
```
function User(name, age) {
      // this = {}
  this.name = name
  this.age = age
  this.isHuman = isHuman
      // return this
}
const user = new User('Simone', 27)
```
### Class
A função também pode ser escrita assim:
```
class User {
  constructor(name, age) {
    this.name = name
    this.age = age
    this.isHuman = isHuman
  }
}
const user = new User('Simone', 27)
```
E criar funções dentro do Construtor:
```
class User {
  constructor(name, age) {
    this.name = name
    this.age = age
    this.isHuman = isHuman
  }
  printName() {
    console.log(this.name)
  }
}
const user = new User('Simone', 27)
user.printName()
```
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

### Async vs Defer
- Quando voce coloca a tag script no final do Body, o download do script só começa a ser feito no final do carregamento da pagina 
- Colocar no Head com a propriedade 'defer' para que o JS seja executado assim que abrir a pagina
```
<head>
  <script defer src=''></script>
</head> 
```

