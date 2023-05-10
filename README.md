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

# Análise e Conclusões
## Metodologia
O algoritmo de jogador de força consiste em selecionar e filtrar um grupo de palavras que se enquadre nas informações que o jogador possui até o momento. Por exemplo, o jogador já inicia sabendo o tamanho da palavra que deve descobrir, e a partir disso, já restringue seu range de palavras. Com um grupo de palavras selecionado, utilizamos um algoritmo de Huffman para elencar as letras mais frequentes dentro desse acervo, e para consequentemente chutar a mais provável de acertar. 

## Resultado Encontrado

