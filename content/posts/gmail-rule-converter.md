---
author: "Carlos Rabelo"
title: "GRC — Gmail Rule Converter"
date: "2023-09-28T09:00:00"
description: "Quando a caixa de entrada transborda, um arquivo YAML pode valer mais que mil cliques."
tags: ["gmail", "produtividade", "ferramentas", "open-source"]
---

Minha caixa de entrada no trabalho parece um terminal de alertas. Sistemas, notificações, monitoramento, comunicados internos, mensagens de equipe — centenas de emails por dia, cada um competindo por atenção.

No começo tentei domar aquilo pelos filtros do Gmail. A interface parece simples até o dia em que você tem vinte regras. Depois trinta. Depois cinquenta. Em algum ponto você para de ler email e passa a gerenciar filtros — clicar, colar, selecionar, salvar, repetir. De novo. E de novo.

Até que cansei. Rabisquei umas ideias no meu Common Place Book: e se cada filtro fosse uma linha num arquivo de texto? Sem formulários, sem cliques, sem abas. Algo que eu pudesse versionar, revisar e replicar sem enlouquecer.

Foi assim que nasceu o [`grc`](https://github.com/carlosrabelo/grc) — **Gmail Rule Converter**. Você escreve os filtros em YAML:

```yaml
rules:
  - name: Newsletters
    author: "newsletter@"
    action:
      label: "Newsletters"
      skipInbox: true

  - name: GitHub
    author: "@github.com"
    subject: "notification"
    action:
      label: "GitHub"
      markRead: true
```

E gera o XML para importar no Gmail com um comando:

```bash
grc gmail filters.yaml
```

No caminho, o `grc` aprendeu a entender expressões de busca (`from:`, `subject:`, `OR`, negação), validar sintaxe antes de gerar o XML, e fazer o caminho inverso — converter o XML do Google Takeout de volta para YAML. Atom feeds e URLs de busca saíram naturalmente do mesmo YAML, então entraram também.

### O que eu não esperava

A maioria dos meus colegas — que não são da área de tecnologia — nem sabia que filtros de email existiam. Mostrei como funcionava, configurei algumas regras básicas para quem estava visivelmente sobrecarregado. Para eles, aquilo não era "criar um filtro", era mágica.

O projeto nasceu para resolver um problema meu. Acabou ajudando outras pessoas também.

O repositório está no [GitHub](https://github.com/carlosrabelo/grc).
