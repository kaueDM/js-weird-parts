# Processador Sintático

Software que converte o código (Javascript ou não) para algo que possa ser
entendido pelo computador.


#Ambientes Léxicos

A ordem ou posicionamento de cada comando e elemento dentro do código. A
composição léxica de um código pode gerar resultados diferentes, tendo em vista
a forma que o processador sintático vai compreender o código.


#Contexto de Execução

A forma como o código é executado. A partir de diversos ambientes léxicos, o
contexto de execução define a ordem que o código vai ser executado.

Esse contexto se divide em duas fases: Criação e Execução

Os exemplos aqui apontados ilustram o contexto **GLOBAL**

###Criação
A engine Javascript cria um objeto global (chamado **window** no caso dos browsers),
uma variável global chamada **this**, define o ambiente externo (ainda não estudado)
e faz a alocação na memória de todas as funções e variáveis.

>No contexto GLOBAL, 'window' e 'this' são a mesma coisa.

Enquanto funções são alocadas inteiramente na memória, as variáveis tem apenas
seu nome armazenado, tendo como valor 'undefined'. Por esse motivo, quando uma
variável é chamada no código antes mesmo de ter seu valor definido, retorna
'undefined'

**'undefined' é uma palavra reservada do Javascript**

###Execução
Momento onde o Javascript lê o código escrito pelo desenvolvedor, definindo valores
para variáveis, etc.

#Hoisting

'Içamento', onde o Javascript move as funções e variáveis para o topo do código,
onde funções podem ser executadas antes mesmo de existirem.

Na prática, o 'Hoisting' ocorre durante a fase de criação do Contexto de Execução,
ou seja, **o Javascript não 'move' o código,ele lê os dados previamente alocados na
memória**.

###Código 01 - Hoisting
>console.log(a);
>var a = 'foo';
>
>//Resultado: undefined

A variável é alocada na memória e recebe por padrão o valor **undefined**
Como o valor é passado após a execução do *console.log()*, é mantido o valor
existente na memória, ou seja, **undefined**

###Código 02 - Sem valor específico
> var a;
>console.log(a);
>
>//Resultado: undefined

A variável 'a' é alocada na memória e recebe por padrão o valor **undefined**
Como nenhum valor foi definido anteriormente, é mantido o **undefined**

###Código 03 - Resultado esperado
>var a = 'foo';
>console.log(a);
>
>//Resultado: foo

A variável 'a' é alocada na memória e recebe por padrão o valor **undefined**
No início da execução, é declarado o valor **foo** para a variável, fazendo com que
o *console.log()* retorne **foo**

###Código 04 - Erro
>console.log(a);
>
>//Resultado: Uncaught ReferenceError: **a** is not defined

O contexto de execução é criado sem armazenar qualquer variável na memória
Ao tentar retornar **a**, que não existe, a engine retorna um erro.

~~Updates conforme o progresso do curso.
