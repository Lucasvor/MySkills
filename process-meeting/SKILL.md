---
name: process-meeting
description: Processa videos, arquivos SRT ou transcricoes de reuniao em um workspace continuo de projeto. Use quando o usuario quiser transcrever reuniao, transformar conversa em memoria de projeto, atualizar glossario/backlog, gerar ata com evidencias, ou criar um relatorio didatico que ensine leitores leigos sem inventar fatos.
---

# Process Meeting

Transforme uma reuniao bruta em memoria de projeto: transcricao, glossario, decisoes, pendencias, evidencias e um relatorio claro. Prefira o modo didatico com grounding rigoroso, mas deixe o usuario escolher o estilo final.

## Principios

- Seja fiel aos arquivos e a transcricao. Nao use conhecimento corporativo, nomes de pessoas, siglas internas ou contexto de projeto sem fonte local ou confirmacao do usuario.
- Ensine sem inventar. O relatorio pode explicar, organizar, criar analogias e traduzir jargoes, mas nao pode criar fatos novos.
- Separe fato, inferencia e duvida. Toda afirmacao importante deve ter tipo de fonte.
- Pergunte antes de consolidar quando faltar contexto que afeta decisoes, tarefas, donos, prazos ou definicoes.
- Preserve rastreabilidade. Decisoes e tarefas importantes precisam apontar para evidencia da transcricao, arquivo local ou resposta do usuario.
- Ajude leitores novos. Termos que podem confundir precisam ganhar uma explicacao curta no markdown e uma camada de tooltip/glossario no site.

## Entradas Aceitas

Aceite qualquer uma destas entradas:

- Caminho de video: rode Whisper e gere SRT antes da analise.
- Caminho de `.srt`: leia a transcricao existente.
- Caminho de `.txt` ou `.md`: trate como transcricao bruta.
- Texto colado pelo usuario: processe diretamente.

Se houver mais de uma reuniao relacionada, pergunte se deve processar como uma unica reuniao consolidada ou como reunioes separadas.

## Workflow

### 1. Preparar workspace

No diretorio do projeto, garanta estes arquivos:

- `PROJECT-MISSION.md`: objetivo macro do projeto/time.
- `TEAM-GLOSSARY.md`: siglas, jargoes, sistemas, pessoas, areas e papeis.
- `ACTION-ITEMS.md`: backlog continuo das pendencias vindas de reunioes.
- `MEETING-RECORD.md`: historico das reunioes processadas.

Se algum arquivo nao existir, crie com estrutura minima e avise o usuario em uma frase curta. Use o formato em [references/WORKSPACE-FILES.md](references/WORKSPACE-FILES.md).

### 2. Obter transcricao

Se a entrada for video, rode o Whisper usando o comando local conhecido pelo usuario:

```powershell
& "D:\1 - Programas\LLPlayer\Whisper\Faster-Whisper-XXL\faster-whisper-xxl.exe" `
  --output_dir "D:\Documentos\Visual Studio 2022\Projects\Projeto autorization\Legendas" `
  --output_format srt `
  --verbose True `
  --beep_off `
  --model large-v3-turbo `
  --model_dir "D:\1 - Programas\LLPlayer\whispermodels" `
  --language pt `
  --device cuda `
  -ct float16 `
  "VIDEO_PATH"
```

Use timeout longo. Se o SRT ja existir, pergunte se o usuario quer reaproveitar ou retranscrever. Se o Whisper falhar por GPU/VRAM/caminho invalido, explique o erro sem continuar como se houvesse transcricao confiavel.

### 3. Normalizar evidencia

Ao ler SRT:

- Remova numeros de legenda e timestamps do texto final.
- Preserve o suficiente da fala original para citar trechos curtos.
- Agrupe falas proximas por assunto quando isso ajudar a leitura.
- Nao invente nomes de falantes se o SRT nao tiver identificacao.

Monte uma lista interna de evidencias com:

- `id`: `E1`, `E2`, `E3`...
- `snippet`: trecho curto da transcricao.
- `topic`: assunto provavel.
- `supports`: decisao, duvida, tarefa ou definicao sustentada.

### 4. Cruzar com memoria local

Leia `PROJECT-MISSION.md`, `TEAM-GLOSSARY.md`, `ACTION-ITEMS.md` e `MEETING-RECORD.md`.

Cruze a transcricao com esses arquivos:

- Pessoas mencionadas: confirme papel, area ou se sao apenas citadas.
- Siglas e jargoes: confirme significado no glossario.
- Sistemas/projetos: confirme se fazem parte da missao atual.
- Tarefas antigas: veja se algo citado altera status, prioridade, escopo ou dono.
- Decisoes passadas: detecte contradicoes ou mudancas de direcao.

Nao corrija automaticamente o estado se houver ambiguidade relevante.

### 5. Escolher modo de relatorio

Antes da geracao final, determine o modo. Se o usuario nao escolher, use `didactic-grounded`.

- `didactic-grounded` recomendado: relatorio claro, gostoso de ler, com mini-aula, glossario simples, contexto e evidencias.
- `faithful-record`: ata mais seca, focada em fatos, decisoes, acoes e riscos.
- `executive-brief`: resumo curto para lideranca, com impacto, decisoes, riscos e proximos passos.

Nao pergunte pelo modo se o usuario ja pediu explicitamente um estilo. Por exemplo, "faz bem didatico" implica `didactic-grounded`.

### 6. Interrogar antes de consolidar

Se existirem lacunas relevantes, pare e pergunte antes de atualizar arquivos ou gerar o relatorio final.

Pergunte apenas o que muda entendimento, decisao, tarefa, dono, prazo, glossario ou escopo. Evite interrogatorio longo por curiosidade.

Organize as perguntas em blocos:

1. Entidades nao mapeadas: nomes, siglas, sistemas, areas ou projetos ausentes no glossario.
2. Tarefas frouxas: combinados sem dono, prazo, criterio de pronto ou dependencia.
3. Status ambiguo: itens antigos do `ACTION-ITEMS.md` que parecem concluidos, alterados, cancelados ou bloqueados.
4. Conceitos arriscados: termos que podem gerar modelagem errada se forem mal entendidos.

Inclua uma recomendacao quando fizer sentido. Exemplo:

```md
1. "Jordane" e "Jordani" parecem ser a mesma pessoa?
   Recomendacao: tratar como a mesma pessoa no glossario, com grafia preferida "Jordani", se voce confirmar.
```

Regra critica: se perguntas bloqueantes foram feitas, pare e espere a resposta do usuario antes de atualizar estado e gerar o relatorio final.

### 7. Atualizar estado

Apos a resposta do usuario:

- Atualize `TEAM-GLOSSARY.md` com definicoes curtas e fonte: `transcript-backed`, `user-confirmed`, `workspace-backed` ou `open-question`.
- Atualize `PROJECT-MISSION.md` somente se a reuniao mudar objetivo macro, escopo ou criterio de sucesso. Se for uma mudanca grande, confirme antes.
- Atualize `ACTION-ITEMS.md` sem duplicar tarefas antigas. Marque alteracoes de status quando a reuniao confirmar mudanca.
- Atualize `MEETING-RECORD.md` com data, titulo, entrada usada, modo de relatorio e link do arquivo final.

### 8. Gerar artefatos finais

Gere sempre os dois artefatos finais, salvo se o usuario pedir explicitamente apenas um formato:

```text
meetings/YYYY-MM-DD-topic-slug.md
meetings/YYYY-MM-DD-topic-slug-site.html
```

Se o projeto ja tiver uma pasta tematica mais apropriada, use essa pasta e explique a escolha no fim.

Use o template do modo escolhido em [references/REPORT-MODES.md](references/REPORT-MODES.md).

O markdown e a fonte canonica do relatorio. O HTML e o companion visual para leitura rapida e ensino. O site deve ser estatico, abrir direto no navegador sem servidor, e conter:

- resumo da reuniao;
- linha narrativa ou mapa conceitual;
- glossario pesquisavel;
- tooltips ou fichas curtas para conceitos que uma pessoa leiga pode nao conhecer;
- decisoes com evidencias;
- acoes;
- pontos nebulosos;
- mini-aula;
- pensamentos futuros;
- mapa de fontes.

Atualize `MEETING-RECORD.md` com os dois caminhos gerados.

## Camada de Conceitos

Em qualquer modo didatico, identifique termos que podem confundir alguem fora da reuniao. Exemplos comuns: nomes de produto, siglas, areas, sistemas, operacoes, status, eventos, prazos e palavras usadas de forma diferente pelo time.

Para cada conceito importante:

- explique em uma frase simples;
- diga como ele aparece nesta reuniao;
- marque a fonte (`transcript-backed`, `workspace-backed`, `user-confirmed`, `agent-inference` ou `open-question`);
- se a definicao ainda nao estiver fechada, escreva `Nao confirmado ainda`.

No markdown, crie uma secao de conceitos. No site, exponha esses conceitos como cards, glossario pesquisavel e/ou tooltips em pontos de leitura onde o termo aparece pela primeira vez.

## Pensamentos Futuros

Inclua uma secao de pensamentos futuros quando houver aprendizados, riscos de modelagem ou proximas decisoes provaveis. Esta secao deve ajudar o time a pensar melhor, mas precisa ser disciplinada:

- nao chame pensamento futuro de decisao;
- marque cada item como `agent-inference`, `open-question` ou `recommendation-from-evidence`;
- conecte a ideia a uma evidencia, duvida ou decisao existente;
- escreva o cuidado/riscos antes de sugerir implementacao;
- se depender de negocio, mesa, area tecnica ou back-office, diga quem precisa validar.

## Regras Anti-Fabricacao

Classifique internamente toda afirmacao importante como:

- `transcript-backed`: diretamente sustentada por trecho da transcricao.
- `workspace-backed`: sustentada por arquivo local do projeto.
- `user-confirmed`: esclarecida pelo usuario durante a interrogacao.
- `agent-inference`: inferida a partir de evidencias, mas nao dita literalmente.
- `recommendation-from-evidence`: recomendacao pratica baseada em decisoes, riscos ou duvidas documentadas.
- `open-question`: ainda sem confirmacao.

Regras obrigatorias:

- Decisoes exigem evidencia da transcricao ou confirmacao do usuario.
- Tarefas exigem acao e fonte. Se faltar dono, use `Sem dono confirmado`. Se faltar prazo, use `Sem prazo confirmado`.
- Definicoes de glossario devem vir de arquivo local, transcricao ou usuario.
- Analogias sao permitidas apenas para explicar conceitos. Elas nunca podem introduzir fatos do projeto.
- Use `Nao confirmado ainda` quando a resposta correta depender de contexto ausente.
- Nao use conhecimento externo de empresa, negocio, sistema ou pessoas, a menos que o usuario solicite.

## Estilo Didatico

No modo `didactic-grounded`:

- Escreva em portugues claro, com frases curtas e ritmo natural.
- Explique "por que isso importa", nao apenas "o que foi dito".
- Use exemplos pequenos quando ajudarem uma pessoa nova no projeto.
- Use humor leve de organizacao, nao piadas que reduzam a seriedade do trabalho.
- Nao infantilize o leitor.
- Evite parecer marketing. O texto deve ser agradavel, mas ainda profissional.
- Se houver jargao inevitavel, traduza na primeira aparicao.

Modelo mental: o relatorio deve permitir que uma pessoa nova leia a reuniao e diga: "entendi o problema, entendi as decisoes, sei o que fazer agora, e sei onde ainda ha duvida".

## Controle de Qualidade

Antes de finalizar, confira:

- Toda decisao tem evidencia ou confirmacao.
- Toda tarefa tem acao, status e fonte.
- Duvidas reais nao foram escondidas.
- O modo didatico nao inventou contexto.
- O glossario foi atualizado com termos realmente uteis.
- O relatorio final ensina o leitor sem perder rastreabilidade.
