---
author: "Carlos Rabelo"
title: "Aprendendo Go com BIP38 — ou: como complicar uma jornada de aprendizado"
date: "2022-04-05T09:00:00"
description: "A melhor forma de aprender uma linguagem é construindo algo que você realmente quer que exista. Mesmo que seja uma ferramenta de criptografia de chaves Bitcoin."
tags: ["go", "programação", "aprendizado", "bip38", "bitcoin", "história"]
---

Sempre gostei de história antiga, e a imagem de César parado diante do Rubicão sempre me fascinou. Atravessar era um ponto sem volta. Não existia "tentar e desistir".

Meu método de aprender linguagens de programação sempre foi o mesmo: escolher um projeto grande demais para o meu nível e simplesmente começar. Atravessar o Rubicão. Depois que o projeto está na sua cabeça, você não pode mais desistir — você precisa terminar.

Foi assim no final dos anos 90, quando eu estava aprendendo Turbo Pascal. Um iniciante faria uma calculadora. Eu resolvi fazer um editor de texto completo — com menus, abrir arquivo, salvar, recortar, copiar, colar. Não fazia ideia do que estava fazendo. Aprendi mais sobre ponteiros, alocação de memória e manipulação de strings do que qualquer livro poderia ter me ensinado. Cada erro era meu, cada segmentation fault era uma lição, cada feature que funcionava era uma vitória.

A mesma lógica se aplicou quando decidi aprender Go em 2022.

### Por que BIP38?

O projeto escolhido foi o [`bip38cli`](https://github.com/carlosrabelo/bip38cli): uma ferramenta de linha de comando para criptografar e descriptografar chaves privadas Bitcoin usando o padrão BIP38. Em vez de um TODO list ou um CRUD qualquer, fui direto para criptografia com scrypt, AES, curvas elípticas secp256k1, Base58Check e um monte de bytes mágicos, checksums e flags de compressão que tornam o padrão extraordinariamente chato de implementar.

Não é exatamente o tipo de projeto que você encontra num tutorial de "Go para iniciantes".

Mas foi exatamente por isso que funcionou. Cada conceito do Go — interfaces, pacotes, testes, tratamento de erros — foi aprendido porque eu *precisava* dele para resolver um problema real. Não era teoria. Era "preciso organizar isso em pacotes porque já está virando uma bagunça" ou "essa interface faz sentido aqui porque amanhã vou implementar outro fluxo de criptografia".

A parte mais tensa foi o debugging. Criptografia não dá erro amigável — ou o resultado bate com os vetores de teste do BIP38 ou você tem um monte de bytes aleatórios. Passei horas comparando hex dumps, relendo a especificação e descobrindo que tinha invertido a ordem dos bytes em algum lugar. Quando o primeiro encrypt/decrypt voltou ao original intacto, foi como acertar um salto mortal.

Tudo isso aconteceu local, sem nenhum commit. Eu não me sentia seguro para publicar — ainda estava aprendendo, o código estava feio em vários lugares, eu não sabia se a implementação estava correta. Ficava adiando, reescrevendo, testando de novo — exatamente como César hesitando antes de atravessar.

Até que chega o dia em que você cruza.

Quando finalmente criei o repositório e subi tudo, foi num commit único. CLI com cobra, implementação completa do BIP38, testes, documentação, Makefile, linter configurado. Tudo junto. Porque aprender uma linguagem nova não deveria ser desculpa para fazer algo pequeno.

### A lição

Se você está aprendendo uma linguagem nova, escolha um projeto que seja **um pouco maior que você**. Não algo tão grande que te paralise, mas algo que te force a aprender coisas que você não sabia que precisava saber.

Atravesse o Rubicão.

O código está no [GitHub](https://github.com/carlosrabelo/bip38cli). E os tutoriais — sim, tem tutoriais — estão em [inglês](https://github.com/carlosrabelo/bip38cli/blob/main/docs/TUTORIAL-EN.md) e [português](https://github.com/carlosrabelo/bip38cli/blob/main/docs/TUTORIAL-PT.md).
