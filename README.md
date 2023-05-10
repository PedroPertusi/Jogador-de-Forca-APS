# Jogador-de-Forca-APS
Por Pedro Pertusi e Alexandre Magno. 

# Descrição
O projeto consiste em desenvolver, implementar um jogador de forca e avaliar seu desempenho para diversas palavras.

# Como utilizar
* É possível instalar a aplicação de duas formas:
  - Clonagem do repositório utilizando o seguinte comando no terminal: `git clone https://github.com/PedroPertusi/Jogador-de-Forca-APS`.
  - Ou baixar o arquivo zip desse repositório em `Code > Download Zip`. E descompactá-lo onde preferir.
* Em seguida, execute o comando: `pip install -r requirements.txt` no diretório principal do projeto clonado.
* Execute o programa com o seguinte comando: `python demo.ipynb`

# Funcionamento
O algoritmo de jogador de forca trabalha restringindo e filtrando o grupo de palavras que se enquadre nas informações que possui até o momento. Na rodada inicial, o jogador já começa com a informação do tamanho da palavra que deve descobrir, e a partir disso, já pode restringir seu range de palavras. Com um grupo de palavras selecionado, utilizamos a primeira etapa do algoritmo de Huffman para elencar as letras mais frequentes dentro desse acervo, e para consequentemente chutar a mais provável de acertar. 

Nosso jogador de forca utiliza dois recurosos para encontrar a resposta final: O primeiro deles, é a capacidade de utilizar as informações que capta a cada rodada para filtrar palavras possíveis. Os critérios de restrição são os seguintes: Tamanho da palavra alvo, letras corretas e incorretas e posição dos caracteres encontrados. Exemplo, para a palavra "arara", caso chute "a" será capaz de encontrar a posição dos caracteres: a_a_a. Dessa forma, selecionará apenas palavras que contemplem essa informação anterior, ficando mais próximo da resposta.

O segundo recurso utilizado é se basear no conceito de eliminação por poncentagem e sua recompesa. Um exemplo, caso após a ordenação por caracteres encontre que a letra "a" seria a tentativa mais provável com 10% de chance, ele fará esse chute. No caso de erro, ele perderá uma vida mas será capaz de eliminar o caracter mais comum, ou seja, restringirá ao máximo possível seu escopo. Caso acerte, encontrará um novo caracter válido e suas posições, assim, chegará mais próximo da resposta, mesmo restringindo pouco.

## Ordenação de Caracter
O algoritmo de ordenação de caracteres funciona da seguinte maneira: conta a quantidade de repetições de um caracter para uma lista de palavras selecionadas, em seguida calcula a probalidade de ocorrência: `quantidade / total_de_letras`, repetindo esse processo para cada letra do alfabeto. Essa é uma etapa inicial do algoritmo de Huffman, que em seguida, criaria uma árvore para atribuir códigos binários de tamanho variável a cada símbolo presente, resultando em compressão dos caracteres. Entretanto, essa parte final não foi necessária para nosso problema.

## Resultado Encontrado

