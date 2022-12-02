# Busca do trajeto mais seguro de um relevo qualquer
Introdução a Otimização (COM361)

Professor Amit Bhaya 
2022.2

Henrique Marques Lozano (henriquemarques@poli.ufrj.br)

Matheus Gomes Rocha (matheusxvtb@poli.ufrj.br)

## Introdução

Nem sempre o caminho mais curto é o mais seguro. Segurança pode ser definida de diversas formas, para os fins desse trabalho, essa ideia vai corresponder à menor mudança de energia potencial, o que corresponde a menor mudança em altura — esta pode ser calculada pela raiz da soma dos quadrados (norma 1). 

O relevo pode ser modelado como uma função polinomial tal que:
$$
f:\mathbb{R}^2 \rightarrow \mathbb{R}
$$

Diversos relevos podem ser gerados com uma função generalizada.

E o caminho pode ser definido com ajuda da gradiente do relevo. Ainda, deve-se definir o melhor algoritmo para buscar o gradiente e ajustar os parâmetros associados. 