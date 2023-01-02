\begin{aligned} 
\text{Neste seção, os resultados obtidos serão exibidos e discutidos.}\\
\end{aligned}


Não obstante, vamos começar pelo primeiro exemplo(Sr. Gato e o Sr. Rato). O problema em questão se dá por essa matriz:


\begin{vmatrix}
  & A & B & C & D &E\\

A & 0 & 2.1 & \infty & 1 & \infty\\

B & \infty & 0 & 1 & \infty & \infty\\

C & \infty & \infty & 0 & \infty & \infty\\

D & \infty & \infty & \infty & 0 & 1\\

E & \infty & \infty & 1 & \infty & 0\\
\end{vmatrix}

Colocando essa matriz no nosso código, obtemos a seguinte formulação:
<p align="center">
  <img width= "470" src="assets/to_readme/Matriz_de_conexão_Ex_1.png">
</p>

No momento em que o código se inicia, ele devolve esses valores:

<p align="center">
  <img width= "470" src="assets/to_readme/Resultado_Ex_1.png">
</p>

O que condiz exatamente como o esperado! o caminho feito por ele foi exatamente esse:


<p align="center">
  <img width= "470" src="assets/to_readme/ezgif.com-gif-maker.gif">
</p>
(Imagem ilustrativa do resultado.)

\begin{aligned} 
\text{O resultado final foi satisfatório para um exemplo simples!}\\ \\
\end{aligned}

### 4.2. **Segundo Exemplo** 

\begin{aligned} 
\text{Para o próximo exemplo, utilizaremos mais arestas para testarmos se o código está de fato funcional:}\\ \\
\end{aligned}

<p align="center">
  <img width= "470" src="assets/to_readme/exemplo_2.png">
</p>


A sua matriz de conexões se dá por:

\begin{vmatrix}
  & A & B & C & D &E\\

A & 0 & 5 & \infty & 1 & \infty\\

B & \infty & 0 & 5 & \infty & 2\\

C & \infty & \infty & 0 & \infty & \infty\\

D & \infty & 2 & \infty & 0 & 5\\

E & \infty & \infty & 1 & \infty & 0\\
\end{vmatrix}

Novamente colocando a matriz em nosso código, obtemos a seguinte formulação:

<p align="center">
  <img width= "470" src="assets/to_readme/Matriz_de_conexão_Ex_2.png">

</p>
A seguir está o valor final retornado, com uma incerteza de 0,00000003 como no exemplo anterior, foi bem satisfatório:
<p align="center">
  <img width= "470" src="assets/to_readme/Resultado_Ex_2.png">
</p>

\begin{aligned} 
\text{Abaixo está a ilustração do caminho feito:}
\end{aligned}

<p align="center">
  <img width= "470" src="assets/to_readme/ezgif.com-gif-maker_2.gif">
</p>
(Imagem ilustrativa do resultado.)


### 4.3. **Exemplo com Terreno Discreto aleatório.**

  Decidimos realizar um teste mais ousado, geramos um terreno discreto em 3 dimensões para simularmos um morro, o ponto de partida que utilizamos foi o ponto na coordenada xyz=(-0.75, 1.0, 0), e desejamos chegar no ponto (0.0, 0.0, 1), o terreno formado em questão foi:
<p align="center">
  <img width= "470" src="assets/to_readme/Terreno_qualquer.png">
</p>

Após colocar todos os parâmetros, foi gerada uma matriz de conexão bem robusta de 121x121 valores, logo mais, foi retornado o custo de toda a jornada, que se deu por:

<p align="center">
  <img width= "470" src="assets/to_readme/custo_Terreno_qualquer.png">
</p>

E com resultado final e percurso com o seu respectivo contorno:

<p align="center">
  <img width= "470" src="assets/to_readme/contorno_terreno_qualquer.png">
</p>

Não obstante, acreditamos viélmente que o código está de fato funcional, com suas respectivas limitações, tanto com relação ao tempo de processamento e limitações de terreno. Com isso em mente, conseguimos aplicar todo o conhecimento aprendido nesses testes em um novo projeto!


## 4.A. **Pseudo-Robô Carrinho** 

Abaixo, está a criação utilizando toda a técnica e experiência obtida nos exemplos anteriores. A ideia principal por trás desse adendo é fundamentada em princípios físicos e dinâmicos, tal qual, velocidade, impulso, posição, tempo e acúmulo de energia potencial.
 
 
O objetivo do Pseudo-Robô Carrinho é: Sair de um determinado ponto de origem, percorrer o trajeto, utilizar a propulsão para conseguir força e pegar impulso, acumular o máximo de energia potencial e utilizar a mesma para terminar o trajeto, sem utilizar o impulso. (Considere o seguinte exemplo, um menino sobe um morro com uma bicicleta, a partir do momento em que ele chega no topo, não há necessidade dele pedalar para descer e terminar o percurso até chegar no ponto final onde ele quer.) essa é uma das inspirações. o código em questão está abaixo: