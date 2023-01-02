

O problema do caminho mais curto/seguro é talvez o problema mais famoso e importante na otimização de redes. Ele encontra um caminho de um determinado nó de origem para um determinado nó de destino com o/a menor/maior custo/segurança de/do caminho. Mas, no nosso caso, vamos utilizar a altura do nosso relevo, considere como se fosse o esforço para conseguir subir um degrau, ou como no exemplo abaixo, o senhor Gato quer pegar o senhor Rato, mas, ele apenas pode pular em uma altura de 1 bloco, pois, se caso tente pular em um bloco que possui 2.1 de altura, ele certamente cairá e vai se machucar (Por motivos médicos, o Senhor Gato não consegue cair de pé), logo, o caminho mais seguro a se fazer é 'A -> D -> E -> C', esse é um caso especial do problema de fluxo de rede de custo mínimo; portanto, o problema do caminho mais curto pode ser resolvido como um problema de programação linear, e utilizando a otimização de fluxo de custo mínimo. A partir da matriz discreta do terreno, devemos entender, qual o custo de deslocar-se de um ponto A a outro B. Assumindo MRU sem atrito, a unica variacao de energia ocorre com a mudanca de altura. Para esse caso, subir uma altura $ h $ custa a mesma energia que descer ela. Com isso em mente, geramos uma matriz quadrada com linhas que representam os nos de origem e as colunas os nos de saida. Essa matriz é simetrica na diagonal e preenchida pelas diferencas de altura entre pontos adjacentes. um exemplo desse problema é:


<p align="center">
  <img src="assets/to_readme/Cat_and_Rat.png">
</p>




Grafo do problema acima:

<p align="center">
  <img width= "470" src="assets/to_readme/exemplo_1.png">
</p>



E em sua forma matricial:

\begin{vmatrix}
  & A & B & C & D &E\\

A & 0 & 2.1 & \infty & 1 & \infty\\

B & \infty & 0 & 1 & \infty & \infty\\

C & \infty & \infty & 0 & \infty & \infty\\

D & \infty & \infty & \infty & 0 & 1\\

E & \infty & \infty & 1 & \infty & 0\\
\end{vmatrix}


Abaixo, há um modelo matemático simples de problema de custo/esforço mínimo que utilizamos como base a função objetivo:


\begin{aligned}
\min_{Z} \sum_{i=1}^n \sum_{j=1}^n c_{ij} x_{ij} \\
\end{aligned}


Sujeito a:

\begin{aligned}
\sum_{j=1}^n x_{ij} - \sum_{j=1}^n x_{ji} = b_i
\
\text{Para cada nó $i$} 
\begin{cases}
     \sum_{j=1}^n x_{ij} = \text{fluxo sai no nó i}\\
     \sum_{j=1}^n x_{ji} = \text{fluxo chega no nó i}
\end{cases}

\end{aligned}

\begin{aligned}
\ 0 \le x_{ij} \le u_{ij}\ \text{Para cada arco(i, j)}
\end{aligned}



Esse modelo matemático requer uma rede representada por um Dígrafo(orientada) e conectada, onde nos $n$ nós incluem-se no mínimo um nó de fornecimento e no mínimo um nó de demanda, com a variável de decisão é:
\begin{aligned} 
x_{ij} = \text{Fluxo no arco (i, j)}
\end{aligned}

Com os parâmetros :
\begin{aligned} c_{ij} \implies \text{Custo unitário do fluxo em (i, j)}
\end{aligned}

\begin{aligned} u_{ij} \implies \text{Capacidade do fluxo em (i, j)}
\end{aligned}

\begin{aligned} b_{i} \implies \text{Fluxo gerado na rede no nó $i$} \implies \begin{cases} b_i > 0& \text{Se o nó $i$ for um nó de origem.}\\ b_i < 0& \text{Se o nó $i$ for um nó de destino.}\\ b_i = 0& \text{Se o nó $i$ for um nó de intermediário}\\ \end{cases}
\end{aligned}

O problema de transporte, caminho mais curto onde se utiliza o algoritmo de Dijkstra tal esse que é uma possível solução para o problema em que foi proposto, de caminho de mínimo esforço. Funciona fundamentalmente em grafos não orientados e orientados, mas, as arestas em questão apenas podem possuir valores positivos. 

Para a entrada, deverá ser um Grafo ponderado:

\begin{aligned}
 G=(N, E) 
\end{aligned}
E nó origem: 
\begin{aligned}
 O \in N 
\end{aligned}
De modo que todos os custos entre as arestas sejam positivos.

A saída será o comprimento do caminho menos custoso de um nó selecionado de origem:
\begin{aligned}
 O \in N 
\end{aligned}
Para todos os outros nós em questão.

E esse fantástico algoritmo funciona da seguinte forma, ele identifica, a partir do nó de origem qual vai ser o caminho menos custoso entre ele e todos os outros do grafo. No começo, o conjunto de nós subsequentes possuem apenas o nó inicial de origem, na medida que ocorre um avanço no grafo, ele seleciona o próximo nó que está mais perto do inicial, após selecionar, a distancia entre cada nó é atualizada, com base na distancia em relação à origem, com base nesse novo ponto, a distância relativa entre nó final vai ficando cada vez menor, e essa é a sua nova posição.
É notório que, após escolher um nó como origem da pesquisa, o algoritmo de Dijkstra calcula o caminho de menor esforço entre esse nó até os subsequentes do grafo. O procedimento é iterativo entre cada etapa e determinando, na interação 1, o nó mais próximo e menos custoso do nó de origem O, nas proximas iterações, o segundo nó mais próximo do nó O, e assim consequitivamente, até que finalmente se alcance o ponto de de destino, após n iterações.
Considerando que há um grafo orientado G=(N, E) e p é um nó desse grafo G, inicialmente devemos colocar um valor zero à cada estimativa do esforço mínimo do nó de origem e infinito às demais estimativas. 
Mas todos esses casos são ramificações do Problema de Fluxo de Custo Mínimo, para modelar esse problema, é necessário que a rede seja representada por um Dígrafo, que no mínimo um dos nós seja de destino, no mínimo um dos nós seja de destino e todos os restantes sejam intermediários para conectar todos os nós. O custo do fluxo através do arco precisa ser proporcional a quantidade daquele fluxo, onde o custo por unidade de fluxo seja conhecido.

Utilizando o grafo G = (Origem, Chegada) com custos arbitrários nos arcos, o custo de um caminho é a soma de todos os custos dos arcos nesse caminho, considerando sem repetições. Por exemplo, se todos os arcos têm custo 1, o custo do caminho total é igual ao seu comprimento até o destino. Um caminho paralelo, ou uma das ramificações dos caminhos, é mais barato que o caminho que for escolhido, se esse caminho paralelo tiver obviamente um custo menor. Assumimos, por definição, que, se não houver outra ramificação com menor custo em um dos arcos, esse caminho escolhido tem custo mínimo. Se não houver caminho algum entre Origem e chegada, o problema não tem solução. Se em geral todos os custos são positivos, a própria relação entre o comprimento total e o custo de um caminho é totalmente intuitiva, pois qualquer pedaço escolhido é mais barato que o caminho todo. Se no problema houver arcos com custo negativo, então ele representa ganho no sistema. 

Considere o exemplo abaixo:



<p align="center">
  <img width= "470" src="assets/to_readme/exemplo_2.png">
</p>


A imagem acima mostra um grafo com custos positivos em seus arcos, o comprimento geométrico de cada arco na figura é proporcional ao seu custo. Vale a pena notar que, mesmo o caminho (A -> B -> C) seja o mais rápido, pelo fato de exigir apenas 3 etapas, ao todo ele não possui o caminho com custo mínimo, pois não é o mais barato, logo o caminho menos custoso é o (A -> D -> B -> E -> C), de fato exige mais etapas, mas sem dúvidas é o que exige menos custo. Essa é a ideia principal do Caminho por Custo Mínimo que está sendo empregada para o desenvolvimento do algorítmo desse trabalho, e esses 2 exemplos mostrados serão resolvidos até o final do mesmo.