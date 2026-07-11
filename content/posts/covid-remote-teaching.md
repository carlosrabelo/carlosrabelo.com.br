---
author: "Carlos Rabelo"
title: "Noventa dias — um relato do lockdown no IFMT"
date: "2020-06-15T09:00:00"
description: "Faz noventa dias que o campus do IFMT fechou as portas. Nesse tempo, eu ensinei professores a dar aula pelo Meet, criei canais no YouTube, configurei mesas digitalizadoras e automatizei o Google Classroom. Um balanço do que aconteceu — e do que ainda não terminou."
tags: ["covid", "educacao", "ensino-remoto", "ifmt", "google-classroom", "automacao"]
---

Faz noventa dias que o campus Bela Vista do IFMT fechou.

Na sexta-feira, 13 de março de 2020, ainda havia gente nos corredores, alunos na cantina, o burburinho típico de um instituto federal em pleno funcionamento. Na segunda-feira, o campus estava vazio. As orientações falavam em duas semanas de recesso. Depois virou um mês. Depois pararam de dar prazos.

Noventa dias depois, estou aqui escrevendo este relato. E o campus continua vazio.

### O choque

A primeira reação foi de paralisia. O campus não é só salas de aula — é laboratório, é prática, é o professor circulando entre as mesas, o aluno que aprende fazendo, a conversa no corredor depois da aula. Nada disso cabe numa sala do Meet.

Mas a educação não podia parar. E a tecnologia era a única ponte.

Eu sou servidor da área de tecnologia da informação, não professor. Mas quando o mundo inteiro migrou para a internet em uma semana, todo mundo virou TI — e TI virou tudo.

### Por que Meet e YouTube

A primeira pergunta não foi "qual a melhor plataforma de ensino". Foi: o que os nossos alunos têm em casa?

A resposta era simples e definiu tudo: celular. Quase todo aluno tinha um. Nem todos tinham computador, nem todos tinham internet boa — mas praticamente todos tinham um celular na mão.

Isso descartou várias opções. Não podíamos exigir que o aluno instalasse um aplicativo exclusivo de ensino remoto, dependesse de um servidor dedicado que teríamos que manter, ou precisasse de um computador com configuração mínima. Somos uma instituição pública, com orçamento público, em plena pandemia — não havia tempo nem recurso para montar infraestrutura do zero.

Meet e YouTube resolveram tudo de uma vez.

O Meet roda no navegador do celular, não precisa de app dedicado, e o link é só clicar. O YouTube é praticamente universal — qualquer telefone acessa, em qualquer conexão, em qualquer qualidade. Um aluno com 3G precário consegue assistir a uma aula gravada em resolução baixa; numa videochamada ao vivo de uma hora, a mesma conexão ia cair a cada cinco minutos.

E o Google Workspace for Education já estava configurado. Contas institucionais para todo mundo, professores e alunos. Não era uma solução nova para aprender — era uma solução que já existia e só precisava ser usada.

A escolha não foi sobre a tecnologia mais avançada. Foi sobre a tecnologia mais inclusiva. Encontrar o aluno onde ele já estava: com o celular na mão, dentro do ecossistema do Google, sem precisar instalar nada nem depender de servidor nosso.

### Ensinando professores pelo Meet

A primeira missão veio rápida e sem manual: colocar os professores no Google Meet.

O Workspace for Education já estava configurado, com contas institucionais para todo mundo. O problema é que quase ninguém sabia que tinha uma conta, e menos ainda sabia o que fazer com ela.

E foi assim que eu passei a dar aula — para os professores.

A ironia não passou despercebida: ensinando a usar o Meet, pelo Meet. Eu na minha casa, eles nas deles, cada um com um nível diferente de familiaridade com tecnologia, compartilhando tela, mostrando onde clicar, repetindo pela terceira vez como silenciar o microfone.

Montei um esquema de turmas. Agrupei os professores por nível de dificuldade — os que já tinham alguma familiaridade ficavam juntos, avançavam mais rápido; os que nunca tinham participado de uma videochamada iam em outra turma, no ritmo que precisassem. Em vez de um tutorial genérico, adaptava o treinamento para cada grupo. Para os de cálculo e matemática, mostrava como combinar o Meet com um quadro branco digital. Para os de laboratório, discutíamos como substituir a prática por simulações e demonstrações gravadas.

Tinha dia em que a aula era sobre Meet. Tinha dia em que era sobre medo. Professor que dá aula há trinta anos no quadro-negro, de repente travado diante da câmera, sem saber onde colocar as mãos. A tecnologia era o pretexto, mas o que eu estava fazendo mesmo era dar confiança. Mostrar que dava certo, que não iam quebrar nada, que o botão certo estava ali.

Vi colega emocionado no final da primeira aula online — não pela aula em si, mas por ter conseguido. Vi professor de cálculo quase desistir ao tentar escrever uma integral com o mouse. Vi gente que nunca tinha ouvido falar em compartilhamento de tela virar referência para os colegas duas semanas depois.

O suporte não tinha horário. Começava às sete da manhã com uma mensagem no WhatsApp e terminava às dez da noite com a última dúvida resolvida. Os finais de semana viraram dias úteis de tanto professor precisando de ajuda para gravar a aula de segunda.

### YouTube e mesas digitalizadoras

Aulas ao vivo resolvem metade do problema. A outra metade é o aluno que não pôde assistir no horário, que tem internet limitada, que precisa revisar. Cada curso precisava de um canal no YouTube, com playlists organizadas por disciplina e por período.

Criar o canal era fácil. Ensinar a manter — gravar, editar, publicar, organizar — era outra história. E tinha professor que precisava escrever na tela.

Para matemática, física, química, desenho técnico, tentar escrever com o mouse é como tentar pintar com um tijolo. A solução eram mesas digitalizadoras. Busquei modelos acessíveis,configurei as que chegavam, testei compatibilidade com os softwares de quadro branco e com o próprio Meet. Alguns professores compraram por conta própria; outros, a instituição conseguiu providenciar. Cada mesa que chegava e ficava funcionando era uma disciplina a mais que podia ensinar a distância sem virar letra ilegível na tela.

Ensinei também, via Meet, como usar a mesa digitalizadora junto com o compartilhamento de tela. Como desenhar, como alternar entre o roteiro e o quadro, como gravar a explicação e subir no YouTube. De novo: a ferramenta era técnica, mas o trabalho era de paciência.

### Automação

Foi no Google Classroom que a coisa virou código.

O campus tem dezenas de cursos, centenas de disciplinas, milhares de alunos. Cada disciplina precisa de uma turma no Classroom. Cada turma precisa de professor, alunos matriculados, link do Meet, organização. Fazer isso manualmente, um por um, seria semanas de trabalho repetitivo — e provavelmente estaria errado na primeira semana.

Aí o instinto de programador falou mais alto. Em vez de apertar botões, escrevi scripts.

O Google Classroom tem uma API completa. Com algumas chamadas, eu cruzava a base de alunos com a grade de horários, criava as turmas em lote, matriculava alunos automaticamente, convidava professores e configurava o link do Meet em cada sala. O que levaria semanas de trabalho manual saiu em uma tarde de código.

Não foi nada elegante. Scripts de emergência nunca são. Mas funcionaram — e quando a base mudou na semana seguinte, foi só rodar de novo.

### Noventa dias depois

Hoje, noventa dias depois do lockdown, o pior do caos passou. Os professores estão no Meet. Os canais do YouTube existem. As mesas digitalizadoras chegaram — a maioria. Os scripts do Classroom rodam. O ensino remoto de emergência virou rotina.

Mas rotina não significa resolvido.

Os canais do YouTube precisam de organização — não dá para achar uma aula de física do segundo período no meio de trezentos vídeos sem ordem. Os scripts do Classroom funcionam, mas são frágeis: sem tratamento de erros, sem validação, sem logs. Se eu adoecer, ninguém sabe onde a coisa para. E tem professor que ainda resiste, que ainda trava na hora de compartilhar a tela, que ainda manda mensagem às nove da noite pedindo ajuda.

A coordenação é o maior desafio, e não é tarefa técnica — é humana. São dezenas de professores com níveis completamente diferentes de familiaridade com tecnologia, cada um com sua forma de ensinar, suas inseguranças, seus medos. Alguns aprenderam tudo em uma semana e estão produzindo conteúdo melhor do que faziam presencialmente. Outros ainda travam. Meu trabalho é garantir que ninguém fique para trás.

### Sem saber até quando

O que torna tudo mais difícil é que não há data final.

Se alguém dissesse "aguenta até agosto", aguentaria qualquer coisa. Mas ninguém diz. As notícias pioram, os números sobem, as decisões são adiadas. Planejamos mês a mês, semana a semana, às vezes dia a dia.

Noventa dias já passaram. Não sei quantos virão pela frente. Sei que amanhã tem mais aula — e que alguém precisa garantir que ela aconteça.
