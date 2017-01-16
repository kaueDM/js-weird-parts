# Syntax Parser

Software que converte o código (Javascript ou não) para algo que possa ser
entendido pelo computador.


#Lexical Environments

A ordem ou posicionamento de cada comando e elemento dentro do código. A
composição léxica de um código pode gerar resultados diferentes, tendo em vista
a forma que o Syntax Parser vai compreender o código.


#Execution Context

A forma como o código é executado. A partir de diversos Lexical Environments, o
Execution Context define a ordem que o código vai ser executado.


#Global ~> Aquilo que não está dentro de uma função
A engine do Javascript cria dois componentes no contexto de execução global:
Um objeto global e a variável 'this'. No contexto global, ambos são a mesma coisa
e possuem o mesmo valor.

#Hoisting

'Içamento', onde o Javascript move as funções e variáveis para o topo do código,
onde funções podem ser executadas antes mesmo de existirem.

Na prática, o 'Hoisting' ocorre durante a primeira fase de criação do Contexto de
Execução, onde a engine inicializa o objeto global, a variável 'this', o ambiente
externo (conteúdo sobre isso mais pra frente) e faz a alocação de memória para
todas as funções e variáveis criadas. Ou seja, o Javascript não 'move' o código,
ele lê os dados previamente alocados na memória.

Enquanto funções são alocadas inteiramente na memória, as variáveis tem apenas
seu nome armazenado, tendo como valor 'undefined'. Por esse motivo, quando uma
variável é chamada no código antes mesmo de ter seu valor definido, retorna
'undefined'

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
