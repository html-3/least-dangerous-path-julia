# Busca do trajeto mais seguro de um relevo qualquer
Introdução a Otimização (COM361)

Professor Amit Bhaya 
2022.2

Henrique Marques Lozano (henriquemarques@poli.ufrj.br)

Matheus Gomes Rocha (matheusxvtb@poli.ufrj.br)

## Introdução

Nem sempre o caminho mais curto é o mais seguro. Segurança pode ser definida de diversas formas, para os fins desse trabalho, essa ideia vai corresponder à menor mudança de energia potencial, o que corresponde a menor mudança em altura — esta pode ser calculada pela raiz da soma dos quadrados (norma 1). 



Diversos relevos podem ser gerados com uma função generalizada.

E o caminho pode ser definido com ajuda da gradiente do relevo. Ainda, deve-se definir o melhor algoritmo para buscar o gradiente e ajustar os parâmetros associados. 

## 1) Relevo discreto

Define-se o relevo como uma função polinomial tal que:

$$
f:\mathbb{R}^2 \rightarrow \mathbb{R}
$$

A altura é definida em cada ponto no plano bidimensional. Assumir um relevo continuo é computacionalmente viavel mas custoso, a discretizacao do terreno facilita o problema e permite representar o problema como um grapho sem distanciar-se demais da solucao real, considerando intervalos pequenos. Os pontos do terreno podem ter diversas geometrias: triangular, hexagonal ou quadrada, a qual vai ser empregada neste caso. 

## 2) Matriz de conexoes

A partir da matriz discreta do terreno, devemos entender, qual o custo de deslocar-se de um ponto A a outro B. Assumindo MRU sem atrito, a unica variacao de energia ocorre com a mudanca de altura. Para esse caso, subir uma altura $ h $ custa a mesma energia que descer ela. Com isso em mente, geramos uma matriz quadrada com linhas que representam os nos de origem e as colunas os nos de saida. Essa matriz é simetrica na diagonal e preenchida pelas diferencas de altura entre pontos adjacentes.
