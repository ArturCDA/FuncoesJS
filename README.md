# FuncoesJS
Criação de Funções em JS.
## 1. **Declaração de função (Function Declaration)**
### Descrição
  Uma declaração de função (também conhecida como definição de função) é composta por function uma palavra-chave, seguida por um nome de função obrigatório, uma lista de parâmetros entre parênteses (para1,...,paramN) e um par de chaves {...} que delimita o corpo do código.

### Vantagens
+ <ins>**Sintaxe**</ins> - Fornece simplicidade e sendo direta, facilitando a leitura e organização do código.

+ <ins>**Hoisting**</ins> - É útil em algumas situações. Por exemplo, quando você deseja chamar a função no início de uma script. A implementação da função pode ser encontrada abaixo no arquivo, então você nem precisa rolar a tela até lá.

+ <ins>**Utilização**</ins> - Pode ser usada para criar funções que são acessíveis globalmente ou dentro de um escopo específico.

### Desvantagem
+ Menos flexível em funções de condicionamento - Alguns ambientes Java Script geram um erro de referência ao invocar uma função cuja declaração aparece dentro de blocos {...} de instruções if, for ou while.

### Sintaxe
    function name([param,[, param,[..., param]]]) {
       [statements]
    }
`name`

O nome da função.

`param`

O nome de um argumento a ser passado para a função. Uma função pode ter atè 255 argumentos.

`statements`

As instruções que compõem o corpo da função.

#### 1° Exemplo de declaração de função:
    function saudacao (nome) {
      return "Olá, "+ nome + "!";
    }
    
    console.log(saudacao("Artur"));

Uma função criada com uma declaração function é um objeto `Function` e tem todas as propriedades, métodos e comportamentos dos objetos `Function`. 

Por padrão, funções retornam `undefined`. Para retornar qualquer outro valor, a função precisa ter uma instrução <ins>`return`</ins> que especifica o valor para retorno.
#### 2° Exemplo de declaração de função:
### Hoisting
    console.log (dizerOla('Artur'));
    
    function dizerOla(nome) {
        return 'Olá, {nome}! ';
    }
Uma propriedade importante da declaração de função é seu mecanismo de elevação. Ele permite o uso da função antes da declaração no mesmo escopo.

#### 3° Exemplo de declaração de função:
### Regular
A declaração de função é útil quando uma função regular é necessária. Regular significa que você declara a função uma vez e depois a invoca em vários lugares diferentes. Este é o cenário básico:

    function sum(a, b) {
      return a + b;
    }
    
    console.log(sum(5, 6));         // => 11
    console.log([3, 7].reduce(sum)) // => 10
## 2. **Expressão de função (Function Expression)**
### Descrição
Uma expressão de função (function expression) é muito similar e tem quase a mesma sintaxe de uma declaração de função. A principal diferença entre uma expressão de função e a declaração de uma função é o nome da função (function name), o qual pode ser omitido em expressões de funções para criar funções anônimas ou nomeadas.

### Vantagens
+ <ins>**Flexível**</ins> - Útil em expressões, passadas como argumentos ou retornadas de outras funções.

### Desvantagens
+ <ins>**Sem Hoisting**</ins> - Ou seja, se você tentar usar a função antes da linha onde ela é criada, vai dar erro.

+ <ins>**Mais Verboso**</ins> - Para funções bem curtas, uma Function Expression comum é mais "pesada" na escrita.

### Sintaxe
    function (param0, param1, /* …, */ paramN) {
      statements
    }

    function name(param0, param1, /* …, */ paramN) {
      statements
    }

`name`

O nome da função. Pode ser omitido, caso em que a função é anônima . O nome é local apenas para o corpo da função.

`paramN`

O nome de um parâmetro formal para a função.

`statements`

As instruções que compõem o corpo da função.
#### 1° Exemplo de expressão de função:
### Nomeada
    const myFunctionVar = function getNumber() {
      console.log(typeof funName === 'function'); 
      return 42;
    }
    console.log(myFunctionVar());    
    console.log(myFunctionVar.name); 
  
    console.log(typeof getNumber);
      
Quando a expressão tem o nome especificado, trata-se de uma expressão de função nomeada.

function getNumber() {...} é uma expressão de função nomeada. A variável getNumber é acessível dentro do escopo da função, mas não fora. De qualquer forma, a propriedade `name` do objeto de função contém o nome: `getNumber`.


#### 2° Exemplo de expressão de função:
### Anônima
    const name =  (function(variable) {return typeof variable; }).name
    
    console.log(name); 

Esta é uma função anônima, cujo nome é uma string vazia.

Às vezes, o nome da função pode ser inferido. Por exemplo, quando o anônimo é atribuído a uma variável:

    const myFunctionVar = function(variable) { 
      return typeof variable; 
    };
    
    console.log(myFunctionVar.name);

O nome da função anônima é `'myFunctionVar'`, porque `myFunctionVar` o nome da variável é usado para inferir o nome da função.
#### 3° Exemplo de expressão de função:
    var x = function (y) {
      return y * y;
    };

Define uma função sem nome e a atribuia a x. A função retorna o quadrado de seu argumento.

## 3. **Função de seta (Arrow)**
### Descrição
Uma arrow function nada mais é do que uma forma diferente e mais enxuta de escrever certas funções. Além disso, utilizamos o sinal `=> (seta)` para definir a instrução da função e o valor que ela irá retornar.

### Vantagens 
+ <ins>**Sintaxe simples e curta**</ins> - Não precisamos usar a palavra-chave function. Em vez disso, as definimos como variáveis constantes e usamos a função como seu valor e não precisamos escrever explicitamente a palavra return. Podemos simplesmente colocar o valor que será retornado após a seta =>.

+ <ins>**Não possui This próprio**</ins> - Arrow functions não criam um novo contexto de this. Elas herdam o this do local onde foram definidas.

### Desvantagens 
+ <ins>**Menor Clareza em funções grandes**</ins> - Dificulta a leitura e manutenção do código.

+ <ins>**Não tem arguments**</ins> - `arguments`object não está disponível na função de seta (ao contrário de outros tipos de declaração que fornecem argumentsobject). No entanto, você pode usar parâmetros rest (...params).

+ <ins>**Não pode ser usado como método de objetos**</ins> - Expressões de função de seta devem ser usadas apenas para funções que não sejam métodos, pois elas não possuem um método próprio this.

+ <ins>**Não podem ser usados como construtores**</ins> - Funções de seta não podem ser usadas com construtores e gerarão erro quando chamadas com <ins>`new`</ins>. Elas também não possuem uma <ins>`prototype`</ins> propriedade.

+ <ins>**Não podem ser usados como geradores**</ins> - A <ins>`yield`</ins> palavra-chave não pode ser usada no corpo de uma função de seta(exceto quando usada em funções geradoras aninhadas dentro da função de seta). Consequentemente, funções de seta não podem ser usadas como geradoras.

+  <ins>**Quebra de linha antes da seta**</ins> - Uma função de seta não pode conter uma quebra de linha entre seus parâmetros e sua seta.

#### 1° Exemplo de função de seta:
### Subtração
    const subtracao = (a,b) => a - b;

#### 2° Exemplo de função de seta:
### Soma
    const somar 2 = a => a + 2;

#### 3° Exemplo de função de seta: 
    const Pessoa = (Artur) => {
      return {
        nome: Artur,
        falar: () => {
          console.log(`Olá, meu nome é ${Artur}`);
        }
      };
    };
