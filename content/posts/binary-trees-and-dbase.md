---
author: "Carlos Rabelo"
title: "Árvores binárias, bancos de dados e 38 anos de distância"
date: "2023-09-17T10:00:00"
description: "Em 1985, um artigo da Micro Sistemas me ensinou o que era uma árvore binária. Em 2023, implementei uma em Go num clone de dBase II. Entre os dois momentos, a mesma ideia — só mudou a ferramenta."
tags: ["go", "programacao", "aprendizado", "dbase", "arvore-binaria", "historia"]
---

No meio da implementação do [`gobi`](https://github.com/carlosrabelo/gobi) — meu clone de dBase II em Go — cheguei na parte mais interessante: o motor de índices.

O formato `.ndx` do dBase II é uma B-Tree em disco com páginas de 512 bytes, nós que se dividem quando ficam cheios, busca binária navegando pela árvore. Cada nó folha aponta para um registro no arquivo `.dbf`. Cada nó interno aponta para outros nós. É simples, elegante e funciona até hoje.

Enquanto eu escrevia o código em Go, veio à mente a lembrança de um artigo antigo. Não era déjà vu — era memória real, de 38 anos atrás.

### 1985, 15 anos

Micro Sistemas 041, fevereiro de 1985. Eu tinha 15 anos e devorava cada edição da revista. Artigos sobre CP/M, TRS-80, interfaces, linguagens — tudo que um garoto curioso podia querer estava ali.

Naquele número, Ivan Camilo da Cruz publicou a primeira parte de "Um gerente prático em banco de dados". Era um sistema de banco de dados escrito em BASIC para a linha TRS-80, com um recurso que me fascinou na hora: indexação por árvores binárias.

O artigo dizia:

> "A indexação de banco de dados é uma técnica de programação que permite organizar e selecionar fichas do banco. O método de indexação empregado são árvores binárias."

Eu li essa frase dezenas de vezes. Passei horas com papel quadriculado simulando a inserção de nós, desenhando os galhos, entendendo como um nó pai apontava para dois filhos, como a busca descia pela árvore até encontrar o registro certo. Não era só algoritmo — era a primeira vez que eu entendia como um computador podia encontrar dados sem ler tudo do começo ao fim.

O programa era o MSLBD — Mini Sistema de Gerenciamento de Bancos de Dados. As variáveis em BASIC estavam impressas na revista: `E1` era o elo com o galho direito, `E2` o elo com o galho esquerdo, `E3` o elo com o nó pai. E1$, E2$, E3$ — as versões em string porque o BASIC do TRS-80 armazenava ponteiros como números em ponto flutuante e era mais seguro guardá-los como strings.

Na época, eu digitei o programa inteiro da revista no CP-500 da escola. Linha por linha. E rodei. Funcionava.

Depois vieram as partes 2 e 3 — Micro Sistemas 043 e 047 — com as rotinas portáveis e os geradores de etiqueta e mail merge. Cada artigo aprofundava um pouco mais o funcionamento interno. A tabela de descrição de campos, o mecanismo de busca binária, a estrutura dos arquivos de índice.

Foi ali que aprendi banco de dados. Não na faculdade, não num livro teórico — num artigo de revista, numa linguagem que eu mal dominava, digitando linha por linha num micro emprestado.

### 2023, 38 anos depois

Trinta e oito anos depois, estava eu implementando a mesma ideia em Go. A diferença é que o dBase II original usava uma estrutura de árvore menos genérica que a B-Tree do gobi, mas o princípio era idêntico: dividir o arquivo de índice em nós de tamanho fixo, organizar as chaves em ordem, navegar pelos ponteiros até o registro certo.

Eu podia ter usado uma biblioteca pronta. Go tem dezenas de implementações de B-Tree. Mas não era esse o objetivo — o objetivo era entender, reconstruir, tocar cada peça com as próprias mãos.

Cada linha do NDX writer era uma linha do artigo de 85 revisitada. A diferença é que em vez de variáveis `E1`, `E2`, `E3` em BASIC, eu tinha structs, slices e interfaces em Go. Em vez de um TRS-80 com 48K de RAM, um notebook com 16GB. Em vez de digitar o programa da revista, eu escrevia do zero com base na especificação original.

Mas a ideia central era a mesma. E era linda.

### A lição

Aos 15 anos, eu não sabia que estava construindo uma base que duraria décadas. Para mim, era só um programa legal que eu tinha conseguido fazer funcionar. Não tinha noção de que aquele conceito de árvore binária ia reaparecer dezenas de vezes nos anos seguintes — em sistemas de arquivos, motores de banco de dados, algoritmos de ordenação, estruturas de dados.

Quando comecei o gobi em 2023, eu não planejava reencontrar o Ivan Camilo da Cruz no caminho. Mas estava lá, 38 anos depois, na mesma estrutura de ideias.

Dizem que a gente nunca aprende realmente uma coisa até ensinar. Talvez o mesmo valha para reconstruir. Recriar um sistema antigo não é nostalgia — é a forma mais honesta de entender como aquilo realmente funciona.

O que você aprendeu aos 15 que ainda está dentro de você, esperando a hora certa de reaparecer?
