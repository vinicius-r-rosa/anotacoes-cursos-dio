# Anotações realizadas durante os cursos relacionados a Javascript

## Operadores
### Tipos
- Aritimética
- Atribuição
- Comparação
- Lógica
- Condicional

### Aritimética
Os operadores de aritimética são todos aqueles envolvidos com "cálculos", como por exemplo
- \+  --> adição
- \-  --> subtração
- /   --> divisão
- %   --> módulo (resto da divisão)
- \*  --> mutiplicação
- **  --> exponencial
- ++  --> incrementar 1
- --  --> subtrair 1

### Atribuição
Os operadores de atribuição são aqueles envolvidos a atribuir um valor a uma variável, por exemplo:
- =   --> x = y
- +=  --> x = x + y
- -=  --> x = x - y
- *=  --> x = x * y
- /=  --> x = x / y
- %=  --> x = x % y

### Comparação
Os operadores de comparação são os utilizados para comparar variáveis, são eles:
- ==   --> valor igual
- ===  --> valor E tipo iguais
- !=   --> valores diferentes
- !==  --> valores E tipos diferentes
- \>   --> valor maior que
- <    --> valor menor que
- \>=  --> valor maior ou igual que
- <=   --> valor menor ou igual que

### Lógica
Os operadores de lógica são utilizados para fazer a validação de um lógica, são eles:
- &&   --> operador lógico AND / E
- ||   --> operador lógico OR / OU
- !    --> operador lógico NOT / NÃO

### Condicional
A operação condicional, chamado também de _if ternário_ é utilizado para simplificar a lógica de _if (X) else (Y)_ em uma só linha e é utilizado da seguinte forma:

    (Condição) ? statement1 : statemant2
    Ex:
        (X === Y) ? funçãoImprimeA : funçãoImprimeB
    Isso significa que se X for extritamente igual a Y será realizada a operação "funçãoImprimeA", e caso X seja diferente de Y, será realizado "funçãoImprimeB" 

## Variáveis e tipos
> OBS: a função typeof() é utilizada para verificar qual o tipo de dado está atribuido a variavél de parâmetro.

### Tipos
No javascript existem 2 grandes tipos de dados, os "Primitivos" e os "Não Primitivos";

### Primitivos
- number
- string
- boolean
- trivial
    - null
    - undefined
### Não Primitivos
- object
- array

> OBS: Lembre-se de utilizar template strings!
> 
> Sem Template strings: <br>
> ```
> frase = "Seu nome é" + nome + ", não?"
> ```
> Com Template strings: <br> 
> ```
> frase = `Seu nome é ${nome}, não?`
> ```

> OBS: Pelo devtools do chorme, ao acessar a propriedade "\__proto\__" é possível acessar TODOS os métodos da coisa que está sendo utilizada

### Empty vs Null vs Undefined
**Empty** ocorre quando a variável é declarada vazia, ex:
- let str = "";
- let nmbr = 0;
- let array = [];
- let obj = {};

Todos as variáveis acima estão vazias.

O **null** é utilizado **propositalmente** quando você deseja que uma variável seja nula.

O *undefined* ocorre quando um valor é *indefinido*!

> OBS: Fals**y** values são valores tradados como falsos porém não são to tipo **false**

> OBS: !true engloba null, undefined 

## Functions
### Função anônima
São funções que representam expressões. Variáveis a armazenam. Exemplo:
```
const subtrair = function (a, b) {
    return a - b;
} 

subtrair(3, 1)
``` 
### Função autoinvocável
Uma função autoinvocável, conhecidas como IIFE, são funções que são executadas logo após sua declaração. Sua estrutura é:
```
(
    function declaration here;
)();

```
Um exemplo seria:
```
const subtrair = (
    function () {
        return a - b;
    }
)(3, 1);

console.log(subtrair);
```

### Callbacks
Callback não tem uma sintaxe específica, porém uma função recebe este nome quando uma função é passada como argumento da para outra. Exemplo:
```
const calc = function(operacao, val1, val2) {
    return operacao(val1, val2);
}

const soma = function(val1, val2) {
    return val1 + val2;
}

cons sub = function(val1, val2) {
    return val1 - val2;
}

const resultSoma = calc(soma, 1, 2);
cons resultSub = calc(sub, 1, 2);
```

## Parâmetros
### Parâmetro com valor default
Dependendo de como foi decalrada, uma função pode ou não receber um valor. Para que, quando esse valor não seja passado por parâmtro e mesmo assim haja um valor default, é preciso explicitálo na declaração da variável, como por exemplo:
```
function fazAlgo (param1, param2, num = 1) {
    ...
}
```
Ao utilizar `num = 1` , estamos declarando na função que o parâmetro *num* é "opcional" e que quando ele não for passado, o valor atribuído a ele será 1.

### Objeto "arguments"
Dentro de uma função é possível utilizar um objeto chamado *arguments*, através dele conseguimos verificar quais foram os argumentos passados por parâmetro para a função. Por exemplo:
```
function fazAlgo(){
    console.log(arguments);
    console.log(arguments.length);
    console.log(arguments[x]);
}
```

### Arrays
#### Spread
O *spread* é utilziado para lidar de forma separada com cada elemento de um array. Por exemplo:
```
function soma(x, y, z) {
    return x + y + z;
}

const numeros = [1, 4, 2];

console.log(soma(...numeros));
```
Ao utilzar o *...numeros* (**spread**), o que era parte do array se torna um elemento independente.

#### Rest
*Rest* é a técnica de combinar os argumentos de uma função em um array. Esta técnica só pode ser utilizada na declaração dos parâmetros de uma function. Por exemplo:
```
funciton imprimeTamanho(...args) {
    console.log(args.length)
}

imprimeTamanho();
imprimeTamanho(1, 2, 1, "abc", [1, 2]);
```

### Objetos
#### Object Destructuring
Esta técnica consiste em desestruturar objetos para filtrar apenas os dados que sejam pertinentes aquela operação, evitando assim ter que carregar TODOS os dados de um objeto desnecessariamente. Por exemplo:
```
const usuario = {
    uuid: 1324123,
    userName: "Icegurt",
    fullName: {
        firstName: "Vinicius",
        lastName: "Rosa"
    }
}

function getFullName({ fullName }) {
  return `Nome Completo: ${fullName.firstName} ${fullName.lastName}`;
}
```

Desta forma, a função *getFullName* irá receber apenas os dados referentes a chave *fullName*. Porém, digamos que você queira carregar apenas a chave *firstName* dentro do *fullName*, poderia ser feito:

```
function getFirstNameOnly({ fullName: { firstName: first } }) {
  return `First Name: ${first}`;
}
```

Ao utilizar o "*: first*" estamos apenas atrelando o valor da chave *fullName.firstName* a esta variável *first*. Desta forma não seria necessário ficar utilizando a chave *fullName.firstName* o tempo todo...

### For X For in X For of
O **for** é utilizado para criar um laço de repetição dentro de **elementos iteráveis**, como arrays e strings. Sua sintaxe e um exemplo de sua utilização:
```
// sintaxe:
for (initialization; condition; final-expression) {
   statement
}

// exemplo:
let str = '';

for (let i = 0; i < 9; i++) {
  str = str + i;
}
```

O **for...in** é utilziado para criar um laço de repetição entre **propriedades enumeráveis de um objeto**. Sua sintaxe e um exemplo de sua utilização:
```
// sintaxe:
for (variable in object) {
  statement
}

// exemplo:
const object = { a: 1, b: 2, c: 3 };

for (const property in object) {
  console.log(`${property}: ${object[property]}`);
}
```

O **for...of** é também utilizado para criar laços de repetição entre estruturas/elemtos iteráveis, porém, possuí uma sintaxe mais reduzida. Sua sintaxe e um exemplo de sua utilização:
```
// sintaxe:
for (variable of iterable) {
  statement
}

// exemplo:
const array1 = ['a', 'b', 'c'];

for (const element of array1) {
  console.log(element);
}
```
### While X Do...While
O **while** é utilizado para executar intruções até que a condição determinada seja falsa. Sua sintaxe e um exemplo de sua utilização:
```
// sintaxe:
while(condition) {
    statement;
}

function exemplowhile() {
  let num = 0
 while(num <= 5){
    console.log(num);
    num++;
}
exemploWhile()
// 0
// 1
// 2
// 3
// 4
// 5
```

Ou seja, a sua execução só é feita caso a condição seja verdadeira. Por outro lado, o **do...while** SEMPRE irá realizar A PRIMEIRA instrução/iteração. Sua sintaxe e um exemplo de sua utilização:
```
function exemploDowhile() {
  let num = 6;

  do {
    console.log(num);
    num++;
  } while(num <= 5)
}
               
exemploDoWhile( )
// 6
// Só imprimiu o 6 pois a primeira instrução ocorreu e ao verificar, a condicional foi falsa, então não continuou o laço de repetição.
```

> OBS: Uma *function* dentro de um objeto recebe a denominação de **método**.

### Map X Object
A estrutura **Map** é similar a dos **Objects**, porém, os Maps permitem **CHAVES** de qualquer tipo, enquanto os Objects aceitam apenas strings. 

Ao utilizar Maps é possivel utilizar a propriedade *.size* para verificar a quantidade de chaves o Map possui.

// TODO: Pesquisar mais a fundo

// Perguntar: Pq não é tão utilizado??

### Set X Array
A estrutura de **Set** é simlar a dos **Arrays**, porém, na estrutura de Set não é possível colocar valores repetídos! Os Arrays possuem muito mais métodos e flexibilidades. Um exemplo de Sets:
```
const mySet = new Set();

mySet1.add(1);
mySet1.add(5);  
```

## Manipulando a DOM
DOM é a abreviação de Document Object Model e é este o padrão de como os navegadores acessam e modificam os elementos HTML de uma página, os são aqueles como: <\div>, <\span>, <\a>, <\head>, etc.


### DOM X BOM
O BOM, abreviação para Browser Object Model, se refere tudo aquilo que está contido no objeto Window, como a própria DOM, o histórico, a localização, as janelas, etc. 

Através do JS é possível, buscar um elemento da dom pelo seu id, class ou tag; adicinar/modificar/remover elementos html; alterar a estilização; e principalmente, adicionar eventos! 

> Para mais informações visitar os links: 
>
> [Básicos do HTML DOM](https://w3schools.com/js/js_htmldom_document.asp)
>
> [Eventos](https://www.w3schools.com/jsref/dom_obj_event.asp)

// **TODO:** Projeto de uma página simples com light mode e dark mode utilizando apenas HTML, CSS E Vanilla JS.

// **TODO:** Fazer os cursos: [link 1](web.dio.me/course/primeiros-passos-para-desenvolvimento-web/learning/1f67c48e-d7a7-4b22-9025-c62fc1c5f954/?back=/browse) | [link2](https://web.dio.me/course/conceitos-de-responsividade-e-experiencia-do-usuario-1/learning/9261b941-1d0e-4984-8757-4e2bd8f42ae0/?back=/browse)