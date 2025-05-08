# GrauA-FCG25
## Trabalho Prático do Grau A - Fundamento de Computação Gráfica 01/25

**JOGO** **2D** **SIMPLES** **EXPLORANDO** **ANIMAÇÃO** **POR** **SPRITES**

## Informações gerais

Entrega: até **10/05/2025**, via Moodle

Grupo: Individual ou em grupos de até 3 participantes

O objetivo deste trabalho é desenvolver um protótipo de jogo 2D,
utilizando a API Gráfica OpenGL (moderna), aplicando os conceitos vistos
em aula. Para o Grau A, os conhecimentos sobre *desenho* *de*
*primitivas*, transformações geométricas, projeção ortográfica e
mapeamento de textura serão explorados.

## Instruções de desenvolvimento
O programa deve possuir, como requisitos mínimos:

• Utilizar a API na versão 3.3 ou superior, o que caracteriza que é obrigatória a
implementação de shaders.

• Correta criação e utilização correta dos buffers de geometria 
  - VAO, VBO(s) e EBO (este último é opcional)

• Correta utilização das transformações de projeção e nos objetos 
  - Como está mapeada a matriz de projeção ortográfica 2D?
  - Como são feitas e atualizadas as transformações nos objetos da cena?

#### Sprites como textura mapeadas em polígonos, para o desenho de:

• Personagem, objetos e itens <u>animados</u> (utilizando *spritesheets*) 

• Imagens de fundo (uso de camadas)
  - Em fundos multi-camadas podemos implementar o conceito de *parallax* *scrolling*

• Controle da movimentação do personagem (com input de teclado e/ou mouse)
  - Colisão entre os *sprites* (conceito de *hitboxes*), para ações como coletar itens, tiros etc., conforme a proposta do jogo)

É recomendado que o jogo tenha um arquivo de configuração, para carregar imagens das camadas e demais configurações necessárias.

## SUGESTÕES DE JOGOS

A escolha do tipo de jogo está a critério do aluno. Se estiverem sem nenhuma “inspiração”,
seguem algumas ideias que se encaixam perfeitamente em nosso escopo:

• Talvez o jogo mais simples que contenha tudo que precisamos é daqueles em que caem objetos (por exemplo, de cima pra baixo) e você precisa pegá-los movimentando um outro objeto (por exemplo, esquerda e direita). O primeiro jogo nessa linha foi o Catch do Atari (1977), mas existem milhares de jogos similares, normalmente com maçãs caindo.

• Jogos do tipo endless runner com visão lateral também se enquadram bem no escopo, como por exemplo o do dino do Google

• Jogos antigos de atari ou jogos próprios para fliperama mais antigos
são ótimas pedidas também. Você pode se inspirar em sites como https://www.retrogames.cz/index.php

## EXTRAS (opcionais):

• Implementação do *parallax* *scrolling*

• HUDs com texto (usando, por exemplo, a
[<u>FreeType)</u>](http://www.freetype.org/) • Telas de entrada, de
jogo e *gameover*

• Som (SDL mixer, OpenAL, FMOD etc) 

### Apresentação e entrega

• A apresentação será feita em aula (presencial ou remota, conforme
recomendação da professora). É importante e de grande peso na
avaliação que a dupla esteja sincronizada e entenda toda a
estruturação do código (classes, decisões de implementação). Pontos
que devem ser abordados na apresentação:

•Apresentação do grupo (nomes)

•Estrutura geral do código (classes e/ou funções)

•Estrutura dos buffers e shader(s) (como você especificou os vértices
e seus atributos e como você os envia para os shaders)

•Gerenciamento dos *sprites*: como são armazenadas as informações das
transformações, ID de texturas, infos adicionais

•Como é feito o controle do personagem (teclado e/ou mouse) o Como
são verificadas as colisões

•Como é feita a movimentação de outros objetos do cenário (se houver)

•Como é gerenciada a animação dos sprites (se houver)

•Como são gerenciadas as camadas para o efeito de *Parallax* (se
houver)

•Mostrar o programa em funcionamento (sugestão: pode fazer isso no
início, logo após a apresentação). Se julgar necessário, pode mostrar
em outros momentos junto com a explicação.

#### DOCUMENTAÇÃO É TUDO! Não esqueça de adicionar ao diretório do projeto um arquivo LEIAME.txt com informações pertinentes (como instruções para compilação e uso do programa)

#### COMUNICAÇÃO E COLABORAÇÃO SÃO AS CHAVES PARA O SUCESSO. PROIBIDO FICAR TRANCADO COM DÚVIDAS! Utilize o nosso canal da disciplina no Teams.

## BOM TRABALHO!

Lembre-se que todo problema maior pode ser decomposto em problemas
menores

