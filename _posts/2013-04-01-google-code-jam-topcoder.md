---
layout: post
title: "Google Code Jam, Topcoder e outras competições"
description: ""
category: "events"
tags: ["Google Code Jam", "Competições"]
---

_For English language readers: in Brazil, programming competitions are not
widespread, so some questions arose last week about Google Code Jam. In order
to answer them, I wrote an e-mail that I’m now changing into a blog post._

## Motivação

[Google Code Jam](https://code.google.com/codejam) completa 10 anos em 2013.
Numa das listas que participo, surgiram algumas dúvidas sobre o Google Code Jam
e competições de programação em geral. Depois de escrever uma resposta
completa, eu havia pensado em transformar em post para manter a referência
online e, coincidentemente, me sugeriram isso na lista também. Portanto, segue
quase sem edição, o e-mail enviado.

## Como funciona

[Google Code Jam](https://code.google.com/codejam),
[OBI](http://olimpiada.ic.unicamp.br/), [IOI](http://www.ioinformatics.org/),
[Maratona de Programação](http://maratona.ime.usp.br/),
[TopCoder](http://community.topcoder.com/tc) seguem o mesmo estilo.
É apresentado um problema, geralmente com uma história para descontrair,
a descrição da entrada e o formato da saída. O problema geralmente requer
alguma criatividade para resolver e a dificuldade não está no uso de
ferramentas, mas na lógica do algoritmo a implementar. O que eu quero dizer com
isso é que basta saber a sintaxe de uma linguagem, não precisa conhecer todas
as bibliotecas e frameworks. Eventualmente conhecer uma biblioteca de estrutura
de dados é útil. Por exemplo, melhor usar a STL do que implementar hash na mão.

A descrição do problema geralmente é direta (apesar da história para deixar
mais agradável), mas envolve um pouco de interpretação. Por exemplo, não vai
aparecer “implemente o algoritmo de caminhos mínimos”, mas vai aparecer algo
como “Joãozinho adora andar de bicicleta, mas a bicicleta dele não tem
corrente. Ele quer visitar o máximo de pontos turísticos da cidade, mas só
consegue se mover de pontos mais altos para pontos mais baixos. Dada uma lista
de pontos turísticos, qual conecta com qual, a altitude de cada um e o ponto de
origem, seu problema é fornecer a Joãozinho a rota a seguir de forma que ele
consiga visitar o máximo de pontos turísticos possível.”

Na descrição do problema costuma aparecer já o significado das variáveis
a serem utilizadas. Por exemplo: “dada uma lista de N pontos turísticos e sua
respectiva altitude H e M ligações entre pontos turísticos X Y, significando
que o ponto X e o ponto Y estão conectados por um caminho direto…” Daí já
sabemos que, no restante do problema, N se refere a quantidade de pontos
turísticos, H a altitude, etc. Geralmente é usado depois na descrição da
entrada e nos limites do problema.

A descrição da entrada diz exatamente o formato fornecido. Com isso, não
precisa se preocupar com validações. Continuando no exemplo do Joãozinho, se
o enunciado disser que a entrada será composta por dois inteiros N M indicando
o número de pontos e o número de ligações, seguidos de N altitudes e M pares
X Y, você pode ter certeza que a entrada será exatamente assim, não precisa
validar se o usuário vai digitar uma letra onde era número, ou passar menos ou
mais pontos, etc. Se houver uma string e a descrição disser que serão 200
caracteres, pode declarar feliz em C um char bla\[201\] (string em
C é null-terminated, por isso o 1) que não vai ocorrer buffer overflow.
O objetivo é avaliar seu algoritmo, não é produzir um programa comercial.
Também é apresentado um exemplo de entrada para clarificar a descrição feita.

Após, vem uma descrição da saída, indicando o que o formato que o programa deve
responder. Siga esse formato EXATAMENTE. Se a descrição disser para colocar
Result #n, onde n é o número da instância em execução, coloque Result #n
(Result #1, Result #2, etc). Não coloque Result 1 ou Result number 1 ou
qualquer outra coisa porque não vai passar. Se disser para colocar um número
com duas casas decimais, coloque duas casas. Se disser para colocar uma quebra
de linha após alguma coisa, coloque a quebra de linha. Pense em correção
automática e computador é burro. Considere que sua saída será comparada com
o gabarito via diff. Nem sempre é verdade (há problemas mais complexos que
podem exigir uma comparação mais inteligente, mas não precisa se preocupar com
isso, siga a regra do diff e seja feliz). Se o gabarito diz "result", sua saída
diz ”resultado”, o que um diff vai dizer? São diferentes, portanto, está
errado. Aproveitando, veja o exemplo fornecido e siga EXATAMENTE, incluindo
maiúsculas e minúsculas.

No final, é adicionado o limite para todas as variáveis. Por exemplo, 0 <= N <=
10000. Com isso, você já sabe que não terá mais que 10000 pontos. Se seu
programa vai armazenar esses pontos num vetor, por exemplo, você já sabe que
pode declarar um vetor de 10000 posições. Aproveitando, fica a dica: se puder
usar alocação estática, use alocação estática. Quando eu participei da OBI, eu
poderia ter sido o 6º colocado (em vez de 13º) porque fiz um algoritmo correto
para um problema, mas usei alocação dinâmica, não alocava corretamente para
próxima instância e operava com lixo de memória. Se eu tivesse deixado tudo
estático, teria acertado mais um problema e teria pontuação equivalente ao
competidor que foi o 6º. Os limites apresentados também são úteis para
determinar o algoritmo usado. Por exemplo, se você tem certeza que são poucos
itens, pode resolver algo na força bruta (por exemplo, gerando todas as
permutações e escolhendo a melhor). Se são muitos, você já sabe que vai
precisar de um algoritmo eficiente. Geralmente a escolha dos limites é feita de
forma que a linguagem não faça diferença. Por exemplo, Ruby é mais lento que C.
Isso quer dizer que daria, por exemplo, para passar um algoritmo
O(n<sup>3</sup>) em C, mas só O(n<sup>2</sup>) em Ruby? Não, geralmente eles
colocam um limite tal que, continuando nesse exemplo, O(n<sup>3</sup>) seja
lento para todas as linguagens e O(n<sup>2</sup>) seja aceitável para todas as
linguagens.

A diferença entre as competições é o limite de idade, organização, etc. A OBI,
por exemplo, é para ensino médio. A Maratona é em equipes de 3. Google Code Jam
é individual (a maioria é), e por aí vai. Uma diferença para GCJ é a escolha de
linguagens. A maioria das competições limita a linguagem a poucas. Na minha
época de OBI, por exemplo, era apenas C, C++ ou Pascal. Podia resolver
problemas diferentes em linguagens diferentes, mas cada problema deveria ser
resolvido em uma linguagem apenas. Já a Maratona de Programação aceita Java.
GCJ é mais liberal: você pode resolver em qualquer linguagem que tenha um
compilador/interpretador gratuito disponível. Vale usar a linguagem do Matlab,
por exemplo, desde que use somente as funcionalidades compatíveis com Octave.
Não existe uma versão gratuita do Mathematica, então não pode usá-lo. Vale C,
Pascal, Ruby, Python, até Brainfuck (sim, existe quem resolva o GCJ em
Brainfuck).

## Exemplo de problema

Um exemplo de problema (nunca cairia pois é trivialmente trivial
e estupidamente estúpido):

Joãozinho quer ajudar seu pai a fazer a contabilidade da loja. Para isso,
Joãozinho quer usar o computador como uma calculadora, mas ele não tem nenhum
aplicativo disponível. Sua função é ajudar Joãozinho a criar uma calculadora.
Como Joãzinho processa apenas dois itens por vez, sua calculadora só precisa
somar 2 números por vez.

### Entrada

A entrada será composta por N pares X Y correspondo aos números a serem
somados. O programa é finalizado quando X = Y = 0.

### Saída

A saída deverá apresentar Caso #n: Z, onde n é o número do caso de teste
começando em 1 e Z o resultado da soma, seguido de uma quebra de linha.

### Limites

	0 <= N <= 1000000
	0 <= X,Y <= 100

### Exemplo de entrada:

	2 3
	4 5
	2 0
	1 1000
	0 0

### Exemplo de saída:

	Caso #1: 5
	Caso #2: 9
	Caso #3: 2
	Caso #4: 1001


Agora, um exemplo de solução para o problema acima, em C:

{% highlight C %}
#include <stdio.h>

int main()
{
    int x, y, i = 1;
    while(scanf("%d %d", &x, &y) == 2 && (x || y))
        printf("Caso #%d\n", i++, x + y);

    return 0;
}
{% endhighlight %}

## Preparação

O que é importante para se dar bem? Conhecer bem estrutura de dados (saber
quando usar árvore, pilha, grafo, hash, etc) e conhecer bem algoritmos
clássicos (árvore geradora mínima, dijkstra, busca em largura, etc) e técnicas
de programação (algoritmos gulosos, programação dinâmica, etc). Saber quando
usar cada um e saber combiná-los. Um site bom para se preparar é o
[Topcoder](http://www.topcoder.com/tc). Possui fórum com competidores,
tutoriais, pode-se pesquisar códigos de outros competidores, etc. Também
recomendo a leitura desse
[artigo](http://contest-wiki.csc.kth.se/index.php/How_to_get_better%3F).

## Conclusão

Mesmo quem não gosta de competir, deveria acostumar a resolver problemas
algorítmicos difíceis em um curto espaço de tempo, muito útil para conseguir
emprego nas empresas top. Quer trabalhar no Google? Ou Facebook? É com esse
tipo de problema que vocês vão se deparar nas entrevistas.
