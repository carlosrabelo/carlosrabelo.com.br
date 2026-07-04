---
author: "Carlos Rabelo"
title: "Aprendendo Go com dBase II — ou: recriando 1983 em 2023"
date: "2023-07-17T09:00:00"
description: "Depois do BIP38, o método continuou o mesmo: escolher um projeto grande demais e simplesmente começar. Dessa vez, um clone completo do dBase II — a linguagem que eu usava nos anos 90."
tags: ["go", "programação", "aprendizado", "dbase", "história"]
---

Depois de aprender Go construindo uma ferramenta de criptografia Bitcoin, o Rubicão já tinha sido atravessado. O método estava consolidado: escolha um projeto grande demais para seu nível e comece. Depois que o projeto está na sua cabeça, você não pode mais desistir.

Em 2023, a vez foi do [`gobi`](https://github.com/carlosrabelo/gobi): um clone funcional do dBase II escrito em Go.

### Por que dBase II

Desde 1988 eu uso dBase II, dBase III e Clipper. Clipper especialmente nos anos 90, quando construí sistemas completos com ele — eram programas compilados que rodavam em DOS, com telas de dados, relatórios, índices, tudo que um sistema comercial precisava. Foi a ferramenta que me ensinou lógica de programação, manipulação de arquivos e estruturação de sistemas.

Recriar o dBase II em Go foi uma viagem no tempo. Era revisitar a ferramenta que marcou minha formação como programador e ao mesmo tempo aprender uma linguagem nova fazendo algo que eu conhecia profundamente.

Quem sabe no futuro não saia um clone de dBase III também.

### O que é dBase II

dBase II foi um dos primeiros sistemas de gerenciamento de banco de dados para microcomputadores, lançado em 1983 para CP/M e depois para DOS. Era basicamente um prompt de ponto onde você digitava comandos como `USE pessoas`, `LIST FOR nome = "João"`, `REPLACE salario WITH 5000`. Tinha também um motor de expressões com variáveis de memória, scripts procedural com `DO WHILE`, `IF/ELSE/ENDIF`, `DO CASE`, e um sistema de arquivos próprio (`.dbf`, `.ndx`, `.mem`, `.prg`).

Era o Excel da era pré-Windows — milhões de usuários, incontáveis sistemas comerciais rodando em cima dele.

Eu resolvi recriar isso em Go.

### A loucura

Um clone de dBase II envolve:

- Um parser de expressões completo com precedência de operadores, funções embutidas (`TRIM`, `UPPER`, `LEN`, `SUBSTR`, `VAL`, `STR`, `CHR`, `EOF`, `RECNO`, `DELETED`, `FOUND`...) e operadores lógicos no estilo `.AND.`, `.OR.`, `.NOT.`
- Um parser e escritor físico de arquivos `.dbf` no formato original de 1983, com seus campos de 16 bytes, flags de deleção, terminador 0x0D e registros de tamanho fixo
- Um motor de índices B-Tree em disco com páginas de 512 bytes, divisão de nós e busca binária (formato `.ndx`)
- Um REPL com prompt de ponto, histórico de comandos, edição de linha e um multiplexador de comandos
- Scripts procedural com aninhamento de escopos, resolução de `LOOP`/`EXIT` e pilha de chamadas
- Uma TUI compatível com VT100 com `@ SAY / GET`, `READ`, `BROWSE` com navegação por setas e edição in-line
- Comandos como `JOIN`, `UPDATE`, `TOTAL ON`, `SORT ON`, `APPEND FROM`, `COPY TO`, `SELECT` com áreas de trabalho primária e secundária

Tudo isso em Go, uma linguagem que eu ainda estava aprendendo.

### Como foi

Diferente do bip38cli, que saiu num commit único, o gobi foi construído aos poucos — 144 commits no total, cada um implementando um pedaço específico. O primeiro commit foi só a documentação: README, LICENSE e um TODO.md com 154 linhas de especificação do que precisava ser feito. Depois vieram os tokens, o lexer, o parser de expressões, o evaluator, o leitor de DBF, o REPL, os comandos um a um, o motor de índices, a TUI, os scripts...

Cada commit resolvia um problema real. Cada funcionalidade nova exigia entender mais fundo como o Go funciona — interfaces para polimorfismo nos comandos, goroutines não foram necessárias (dBase II é single-threaded por natureza), mas pacotes, testes, tratamento de erros e a ferramenta de build foram aprendidos na prática.

A parte mais interessante foi implementar o formato `.dbf`. Tive que caçar documentação original do dBase II de 1983, entender a estrutura de cabeçalho de 32 bytes, os descritores de campo de 16 bytes, o terminador 0x0D, o marker de deleção, os records de tamanho fixo com campos Character (espaço-padded), Numeric (ASCII, right-justified) e Logical (T/F/Y/N). Quando o primeiro arquivo DBF escrito pelo gobi foi lido corretamente pelo dBase original, foi uma vitória silenciosa mas enorme.

### A lição

Aprendi mais sobre parsing, sistemas de arquivos legados, B-Trees e protocolos de terminal do que qualquer curso poderia ter me ensinado. E aprendi Go no processo — não fazendo exercícios, mas resolvendo problemas reais.

O mesmo método do Turbo Pascal, do BIP38, e agora do dBase II: atravesse o Rubicão. Depois que você começa, não tem mais volta.

O código está no [GitHub](https://github.com/carlosrabelo/gobi).
