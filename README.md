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

# Resultado Encontrado
## Avaliando o Jogador
Nosso jogador apresentou uma média de acertos de 92%, esse resultado foi obtido em cima de 1000 jogos aleatórios aonde houve 920 acertos e 80 erros, sendo assim nosso jogador apresenta um bom percentual de acertos. Todavia, são os erros que chamam a atenção, visto que as palavras aonde o jogador não consegue acertar ele nunca consiguirá, ou seja, existe um grupo de palavras que o nosso jogador nunca será capaz de acertar, independente do número de tentativas. 

Buscando entender os erros, devemos considerar como nosso jogador opera, ele sempre utiliza de todas as informações disponíveis para tomar suas decisões, sendo elas o tamnho da palavra, as letras chutadas e dentre elas as posições das corretas, e levando em conta essas informações ele é capaz de escolher o montante de palavras analizado (todas presentes devem seguir esses requisitos), e então olhando para esse grupo de palavras ele encontra a letra com maior probabilidade e então escolhe-a. Por tanto, pensando em erros, então as palavras não adivinhadas são palavras que mesmo quando esse grupo de palavras contém mais letras diferentes do que pelo menos uma contida em nossa palavra, e devido ao jogo contar com apenas 5 vidas, ele não é capaz de reduzir o numero de palavras o suficiente, perdendo antes de ser capaz de achar a letra faltante (letra de pouca probabilidade).

## Exemplos

Nesse caso a palavra errada é `fixasses`.
Olhando para a mesma, a letra que mais chama a atenção por conta de sua ausência é a letra `X`, e é justamente ela que deu trabalho a nosso jogador, mas não pelo motivo que pensa. Ele foi capaz de chegar até `fi_asses` tendo errado as letras: 'r','o','m','c' e 'l', com isso quando restou apenas uma letra na palavra a chance era a mesma para todas as letras que poderiam preencher porém podemos imaginar que ele provavelmente optou por `c` e `l` em vez de `x` devido a como nosso algorítimo foi implementado, aonde quando a probabilidade é a mesma ele opta pela ordem alfabética, errando assim apenas por que todas as letras possíveis tinha mesmas chances e então ele escolheu por ordem alfabética.

No caso seguinte a palavra errada é `zunais`.
Nessa caso o motivo de erro é mais simples, é o fato de possuir a letra `Z` de baixa incidência. O jogador até chega a acertar `_u_ais`, porém acaba chutando outras letras com maior incidência como `c` e `f` e por isso acaba perdendo.

No último caso a palavra errada é `coliseu`.
Neste caso o problema é encontrado nas vogais, em especial a vogal `u`, que é a vogal de menor incidência e por conta disso ele acaba não selecionando ela e assim fica mais dificil preencher as letras e reduzir as palavras do grupo. Inclusive, esse é um das possíveis melhorias que poderia ser realizada pelo grupo, nesse caso a priorização das vogais, se a palavra ainda não conter o número de vogal média para uma palavra de tal tamanho.