---
author: "Carlos Rabelo"
title: "act — ou: como parei de fazer commit e comecei a testar GitHub Actions localmente"
date: "2020-11-15T10:00:00"
description: "GitHub Actions é ótimo até você precisar testar. O esquema é sempre o mesmo: commit, push, esperar, falhou, arrumar, commit, push, esperar. Até que um dia encontrei o act."
tags: ["github-actions", "devops", "ferramentas", "produtividade", "automacao"]
---

Eu estava sentado no sábado à tarde, na frente do terminal, assistindo a barra de progresso de um workflow do GitHub Actions subir lentamente. Pela quinta vez.

Commit. Push. Esperar. Falhou.

Arrumar. Commit. Push. Esperar.

GitHub Actions foi lançado em novembro de 2019 e eu abracei a ideia na hora. Finalmente uma ferramenta de CI/CD nativa do ecossistema GitHub, integrada com o repositório, sem precisar configurar webhooks, sem precisar de um servidor Jenkins morrendo aos poucos num canto da rede.

Só tinha um problema: testar.

Qualquer alteração no workflow — um passo quebrado, uma sintaxe errada no YAML, uma variável de ambiente que não existe — era descoberta do pior jeito possível. Depois do commit. Depois do push. Depois de minutos esperando o CI pegar o job, baixar as imagens, executar os passos e finalmente falhar.

O feedback loop era tão demorado que eu comecei a evitar mexer nos workflows com medo de quebrá-los. O que deveria ser produtividade virou um peso. Toda modificação era uma aposta.

Foi numa dessas tardes de frustração que eu encontrei o `act`.

Não lembro exatamente como cheguei no repositório — provavelmente foi um desses dias de "deixar de ser besta e procurar uma solução" no Google. O nome era simples: `nektos/act`. A descrição era direta: "Run your GitHub Actions locally". E o slogan me fez sorrir na hora: "Think globally, act locally".

Alguém tinha passado pela mesma frustração e resolvido do jeito certo.

O funcionamento é engenhoso: o `act` lê seus workflows do `.github/workflows/`, usa a Docker API para criar containers que simulam o ambiente do GitHub Actions, e executa cada passo exatamente como o GitHub faria. As imagens dos runners (ubuntu, windows, macos) são pré-construídas e baixadas na primeira execução. As variáveis de ambiente padrão são configuradas automaticamente. Os segredos você passa como argumento ou num arquivo `.secrets`.

Na prática, você roda `act` no terminal e ele faz exatamente o que o GitHub faria — mas na sua máquina, em segundos, sem um único commit.

Os comandos são intuitivos:

```
act -l              # lista os jobs disponíveis
act                 # roda o evento push
act pull_request    # simula um pull request
act -j test         # roda um job específico
```

Cada execução local que passava era um workflow que eu sabia que ia funcionar no GitHub. Pela primeira vez desde que comecei a usar GitHub Actions, eu podia mexer nos workflows sem medo.

A primeira vez que rodei `act` e vi os passos verdes passando um a um no terminal foi como trocar uma carroça por um carro. O que antes levava três ciclos de commit-push-esperar agora resolvia em trinta segundos olhando o terminal.

Claro que não é perfeito. Algumas actions com dependências muito específicas do ambiente do GitHub podem se comportar diferente. A resolução de DNS dentro dos containers às vezes surpreende. E o Docker tem que estar instalado e funcionando — não é um bônus, é um pré-requisito.

Mas para 95% dos casos — testar sintaxe, validar passos, verificar variáveis de ambiente, executar scripts — o `act` resolve com sobras.

O projeto estava no início em novembro de 2020, mas já funcionava bem. Era open source, escrito em Go, mantido pela comunidade. Exatamente o tipo de ferramenta que a gente encontra quando precisa e se pergunta como viveu sem ela.

Hoje, se vou criar um workflow novo, a primeira coisa que faço não é commit. É `act`.
