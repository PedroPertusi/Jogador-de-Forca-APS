# Jogador-de-Forca-APS
Por Pedro Pertusi e Alexandre Magno. 

# Descrição
O projeto consiste em desenvolver e implimentar um jogador de forca.

# Como utilizar
* É possível instalar a aplicação de duas formas:
  - Clonagem do repositório utilizando o seguinte comando no terminal: `git clone https://github.com/PedroPertusi/Jogador-de-Forca-APS`.
  - Ou baixar o arquivo zip desse repositório em `Code > Download Zip`. E descompactá-lo onde preferir.
* Em seguida, execute o comando: `pip install -r requirements.txt` no diretório principal do projeto clonado.
* Execute o programa com o seguinte comando: `python demo.ipynb`

# Análise e Conclusões
## Metodologia

## Resultado Encontrado

## 


# Avaliando o Jogador
Nosso jogador apresentou uma média de acertos de 92%, esse resultado foi obtido em cima de 1000 jogos aleatórios aonde houve 920 acertos e 80 erros, sendo assim nosso jogador apresenta um bom percentual de acertos. Todavia, são os erros que chamam a atenção, visto que as palavras aonde o jogador não consegue acertar ele nunca consiguirá, ou seja, existe um grupo de palavras que o nosso jogador nunca será capaz de acertar, independente do número de tentativas. 

Buscando entender os erros, devemos considerar como nosso jogador opera, ele sempre considera as informações atuais dadas para ele, sendo elas o tamnho da palavra, as letras chutadas e dentre elas as posições das corretas, e levando em conta essas informações ele é capaz de reduzir o montante de palavras para que todas presentes cumpram esses requisitos, e então olhando para esse novo grupo de palavras ele encontra a letra com maior probabilidade e então escolhe-a. Por tanto, se fomos pensar em erros, então as palavras erradas são palavras que mesmo quando reduzimos esse grupo de palavras sempre á uma ou mais letras com probabilidades maiores do que pelo menos uma contida em nossa palavra, e por conta do jogo contar com apenas 5 vidas, ele não é capaz de reduzir o grupo de palavras o suficiente, perdendo antes de ser capaz de achar a letra faltante (letra de pouca probabilidade).

Agora vamos utilizar um exemplo:

Nesse caso a palavra errada é `fixasses`.
Olhando para a mesma, a letra que mais chama a atenção por conta de sua ausência é a letra `X`, e é justamente ela que deu trabalho a nosso jogador, mas não pelo motivo que pensa. Ele foi capaz de chegar até `fi_asses` tendo errado as letras: 'r','o','m','c' e 'l', com isso quando restou apenas uma letra na palavra a chance era a mesma para todas as letras que poderiam preencher porém podemos imaginar que ele provavelmente optou por `c` e `l` em vez de `x` devido a como nosso algorítimo foi implementado, aonde quando a probabilidade é a mesma ele opta pela ordem alfabética, errando assim apenas por que todas as letras possíveis tinha mesmas chances e então ele escolheu por ordem alfabética.

No caso seguinte a palavra errada é `zunais`.
Nessa caso o motivo de erro é mais simples, é o fato de possuir a letra `Z` de baixa incidência. O jogador até chega a acertar `_u_ais`, porém acaba chutando outras letras com maior incidência como `c` e `f` e por isso acaba perdendo.

No último caso a palavra errada é `coliseu`.
Neste caso o problema é encontrado nas vogais, em especial a vogal `u`, que é a vogal de menor incidência e por conta disso ele acaba não selecionando ela e assim fica mais dificil preencher as letras e reduzir as palavras do grupo. Inclusive, esse é um das possíveis melhorias que poderia ser realizada pelo grupo, nesse caso a priorização das vogais, se a palavra ainda não conter o número de vogal média para uma palavra de tal tamanho.