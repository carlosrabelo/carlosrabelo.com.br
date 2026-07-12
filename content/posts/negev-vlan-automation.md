---
author: "Carlos Rabelo"
title: "Negev — automação de VLANs baseada em MAC"
date: "2025-04-26T09:00:00"
description: "Gerenciar VLANs manualmente em dezenas de switches é repetitivo e propenso a erro. O Negev resolve isso lendo a tabela MAC e atribuindo a VLAN certa a cada porta automaticamente."
tags: ["go", "redes", "automacao", "ifmt", "ferramentas", "open-source"]
---

Gerenciar switches à mão funciona quando você tem um punhado deles. Quando esse número cresce, tarefas repetitivas consomem tempo e abrem espaço para erro humano.

No IFMT, temos switches Cisco IOS e Datacom DmOS espalhados pelos campi. A configuração de VLANs era um processo manual: identificar o MAC do dispositivo conectado, descobrir em qual porta ele estava, lembrar a qual VLAN ele pertencia, configurar. Para dezenas de portas, em vários switches, isso se torna inviável no dia a dia.

Foi pensando nisso que criei o [Negev](https://github.com/carlosrabelo/negev).

### Como funciona

O princípio é simples: cada fabricante de equipamento usa um prefixo MAC único (OUI). O Negev usa esse prefixo para determinar a qual VLAN o dispositivo pertence e configurar a porta do switch automaticamente.

O fluxo é direto:

1. Você define em um YAML o mapeamento entre prefixos MAC e VLANs
2. O Negev conecta no switch (SSH ou Telnet), descobre a plataforma automaticamente
3. Lê a tabela MAC, identifica em qual porta cada dispositivo está
4. Verifica se a porta já está na VLAN correta — se não, configura
5. Opcionalmente, cria ou remove VLANs para manter apenas as permitidas

Tudo começa em modo **sandbox**: o Negev mostra exatamente o que vai fazer sem tocar no switch. Quando você confirma, passa `--write` e ele executa.

### Um pouco da técnica

O Negev é escrito em Go e segue uma arquitetura modular com drivers de plataforma. Cada fabricante tem seu próprio dialeto de comandos — o que funciona num Cisco IOS não funciona num Datacom DmOS. A solução foi criar uma interface `SwitchDriver` que cada plataforma implementa, e um registry que seleciona o driver certo automaticamente.

O suporte inicial cobre:

- **Cisco IOS** — detecção de plataforma, leitura de tabela MAC, switchport mode access, criação e remoção de VLANs
- **Datacom DmOS** — mesmo conjunto de funcionalidades, com a sintaxe própria da Datacom

O sistema de transporte também é plugável (SSH e Telnet), com injeção de sequências de autenticação personalizadas para cada equipamento.

### Onde o Negev se encaixa no IFMT

Antes, a configuração de uma única porta envolvia acesso manual ao switch, navegação pelos menus, digitação de comandos e verificação visual. Com o Negev, centralizamos a configuração em um arquivo YAML e deixamos a ferramenta fazer o trabalho braçal.

O impacto mais imediato foi na **padronização**: todos os switches passam a seguir a mesma configuração, sem desvios. Se um computador novo é conectado em qualquer porta, o Negev identifica o prefixo MAC e coloca na VLAN certa na próxima execução.

### Projeto aberto

O Negev é open source (MIT) e está disponível no [GitHub](https://github.com/carlosrabelo/negev). Se você enfrenta o mesmo tipo de problema — seja numa universidade, empresa ou provedor — fique à vontade para usar, adaptar ou contribuir.
