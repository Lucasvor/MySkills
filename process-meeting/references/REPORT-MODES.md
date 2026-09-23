# Report Modes

Use um destes templates conforme o modo escolhido. Em todos os modos, mantenha evidencias curtas e nao transforme inferencias em fatos.

## Modo `didactic-grounded`

```md
# [Titulo da Reuniao]

**Data:** DD/MM/YYYY  
**Modo:** Didatico com evidencias  
**Entrada analisada:** [video/srt/texto]  
**Participantes identificados:** [nomes confirmados e mencoes relevantes]

---

## Resumo Para Quem Chegou Agora

[Explique em 5-8 linhas o problema, o que mudou depois da reuniao e por que isso importa. Use linguagem simples.]

## A Historia da Reuniao

[Conte o fluxo em formato narrativo curto: problema -> discussao -> decisoes -> proximos passos.]

## Glossario de 30 Segundos

| Termo | Traducao simples | Por que importa | Fonte |
|---|---|---|---|
| [Termo] | [Definicao simples] | [Impacto pratico] | [workspace/transcricao/usuario] |

## Conceitos Que Podem Confundir

| Conceito | Explicacao simples | Como aparece nesta reuniao | Status/Fonte |
|---|---|---|---|
| [Conceito] | [Explique sem jargao.] | [Conecte ao assunto da reuniao.] | [transcript-backed/user-confirmed/open-question/etc.] |

## Decisoes e Topicos

### [Topico]

- **O que ficou decidido:** [fato confirmado]
- **Por que isso importa:** [explicacao didatica]
- **Impacto pratico:** [o que muda para o projeto]
- **Confianca:** Alta/Media/Baixa
- **Tipo de fonte:** transcript-backed / workspace-backed / user-confirmed / agent-inference

<details>
<summary>Evidencia da transcricao</summary>

> [Trecho curto que sustenta a decisao.]

</details>

## Proximas Acoes

| Acao | Dono | Prazo | Status | Fonte |
|---|---|---|---|---|
| [Acao] | [Pessoa/equipe ou Sem dono confirmado] | [Data ou Sem prazo confirmado] | Pendente | [Evidencia] |

## Pontos Nebulosos

- [ ] [Questao ainda nao confirmada e por que ela importa.]

## Pensamentos Futuros

- **[Ideia ou cuidado futuro]**
  - **Por que vale olhar:** [Conexao com decisao, risco ou duvida da reuniao.]
  - **Cuidado:** [O que nao pode ser assumido ainda.]
  - **Tipo:** agent-inference / open-question / recommendation-from-evidence

## Mini-Aula da Reuniao

[Ensine o conceito mais importante da reuniao para alguem novo no projeto. Use uma analogia curta se ajudar. A analogia deve explicar o conceito, nao criar fatos novos.]

## Como Saber se Voce Entendeu

1. [Pergunta curta de revisao]
2. [Pergunta curta de revisao]
3. [Pergunta curta de revisao]

## Mapa de Fontes

| Item | Tipo | Fonte |
|---|---|---|
| [Decisao/tarefa/definicao] | transcript-backed/user-confirmed/etc. | [E1, arquivo local ou resposta do usuario] |
```

### Companion HTML obrigatorio

Depois do markdown, gere tambem:

```text
meetings/YYYY-MM-DD-topic-slug-site.html
```

O site deve ser estatico e abrir sem servidor. No modo `didactic-grounded`, inclua pelo menos:

- navegacao por secoes;
- resumo visual;
- mapa ou linha narrativa;
- glossario pesquisavel;
- tooltips ou cards para conceitos potencialmente desconhecidos;
- decisoes com evidencias;
- acoes e filtros quando fizer sentido;
- pontos nebulosos;
- pensamentos futuros claramente marcados como inferencia/recomendacao;
- mapa de fontes.

Tooltips nunca devem carregar uma decisao nova. Eles apenas explicam conceitos ja presentes no markdown.

Para `faithful-record` e `executive-brief`, gere o companion HTML tambem, mas com menos lirismo: resumo, decisoes/acoes, riscos, duvidas, conceitos essenciais e mapa de fontes.

## Modo `faithful-record`

```md
# [Titulo da Reuniao]

**Data:** DD/MM/YYYY  
**Modo:** Registro fiel  
**Entrada analisada:** [video/srt/texto]

## Resumo Objetivo

[2-4 frases, sem interpretacao alem do necessario.]

## Decisoes

| Decisao | Evidencia | Confianca |
|---|---|---|

## Acoes

| Acao | Dono | Prazo | Status | Evidencia |
|---|---|---|---|---|

## Riscos e Dependencias

| Item | Impacto | Evidencia |
|---|---|---|

## Questoes em Aberto

- [ ] [Questao]
```

## Modo `executive-brief`

```md
# [Titulo da Reuniao] - Executive Brief

**Data:** DD/MM/YYYY  
**Modo:** Executive brief  
**Entrada analisada:** [video/srt/texto]

## Bottom Line

[1 paragrafo com a conclusao mais importante.]

## Decisoes Que Mudam o Projeto

- [Decisao + impacto.]

## Riscos

- [Risco + consequencia.]

## Proximos Passos

| Prioridade | Acao | Dono | Prazo |
|---|---|---|---|

## Duvidas Que Precisam de Decisao

- [Pergunta que precisa de lideranca/negocio.]
```
