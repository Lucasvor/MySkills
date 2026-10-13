# Auditoria de versões das skills — 12/10/2026

## Escopo e critério

A auditoria inicial identificou 21 skills que precisavam de confirmação/atualização. Em 12/10/2026, comparei cada uma diretamente com a versão atual disponível no upstream. Dez tinham diferenças reais e foram sincronizadas; onze já eram idênticas ao upstream. Também sincronizei os destinos canônicos to-tickets e to-spec para manter as entradas antigas to-issues e to-prd compatíveis. Complementos locais de TDD, domínio e tickets foram preservados.

- **Parece atual** significa que o conteúdo local correspondeu à página upstream consultada ou que há evidência de que a revisão upstream visível antecede a cópia local. Como a maioria das cópias não fixa SHA/commit, isso não é uma prova reproduzível de identidade.
- **Desatualizada** significa que encontrei divergência concreta, revisão posterior ou mudança upstream ausente da cópia local.
- **Não verificável** significa que não há versão/SHA local, upstream público identificável, ou que a fonte/endpoint não pôde ser consultado. Isso não significa que a skill esteja desatualizada.

## Resultado

### Sincronização realizada — 12/10/2026

- Dez skills receberam arquivos atualizados do upstream.
- Onze das 21 skills auditadas já coincidiam byte a byte com o upstream e não precisaram de cópia.
- As entradas locais to-issues e to-prd agora usam o conteúdo atual de to-tickets e to-spec, mantendo os nomes antigos como compatibilidade. Os destinos canônicos também foram sincronizados.
- Arquivos locais adicionais foram preservados: CONTEXT-FORMAT.md no domínio, os três guias extras de TDD e as convenções locais de HITL/AFK e implementação de tickets.
- As outras 34 skills continuam sem fonte/revisão verificável; não foram alteradas.

| Grupo | Total | Atual ou sincronizada | Desatualizada | Não verificável |
|---|---:|---:|---:|---:|
| Skills locais A–H | 26 | 14 | 0 | 12 |
| Skills locais I–Z | 25 | 20 | 0 | 5 |
| Sistema e plugins | 17 | 0 | 0 | 17 |
| **Total** | **68** | **34** | **0** | **34** |

## Skills locais A–H

| Skill | Resultado | Evidência e fonte |
|---|---|---|
| animate | Parece atual | Cópia local corresponde à versão visível do upstream [Emil](https://github.com/emilkowalski/skills/blob/main/skills/animate/SKILL.md); sem SHA local. |
| animate-expo | Parece atual | A inclusão upstream em 18/08 antecede a cópia local; [Emil](https://github.com/emilkowalski/skills/blob/main/skills/animate-expo/SKILL.md). |
| animation-vocabulary | Parece atual | Cópia local corresponde à página upstream consultada; [Emil](https://github.com/emilkowalski/skills/blob/main/skills/animation-vocabulary/SKILL.md). |
| apple-design | Parece atual | Rebuild upstream em 09/07/2026 antecede a cópia local; [Emil](https://github.com/emilkowalski/skills/blob/main/skills/apple-design/SKILL.md). |
| emil-design-eng | Parece atual | Cópia corresponde à página upstream consultada; [Emil](https://github.com/emilkowalski/skills/blob/main/skills/emil-design-eng/SKILL.md). |
| find-animation-opportunities | Parece atual | Última alteração upstream visível em 21/07, antes da cópia local; [Emil](https://github.com/emilkowalski/skills/blob/main/skills/find-animation-opportunities/SKILL.md). |
| diagnose | Parece atual | Cópia local e [upstream](https://github.com/thecloudexplorers/skills/blob/main/skills/diagnose/SKILL.md) têm 117 linhas e conteúdo correspondente; sem SHA/tag. |
| design-taste-frontend-v1 | Parece atual | O changelog upstream diz que a v1 foi preservada sem alterações; [skill v1](https://github.com/Leonxlnx/taste-skill/blob/main/skills/taste-skill-v1/SKILL.md). |
| high-end-visual-design | Parece atual | Descrição e 98 linhas correspondem ao arquivo upstream atual; [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/soft-skill/SKILL.md). |
| hallmark | Parece atual | Versão local/upstream 1.1.0; 558 linhas em ambos. [Skill](https://github.com/Nutlope/hallmark/blob/main/skills/hallmark/SKILL.md) e [package.json](https://github.com/Nutlope/hallmark/blob/main/package.json). |
| code-review | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Matt Pocock](https://github.com/mattpocock/skills/blob/main/skills/engineering/code-review/SKILL.md). |
| diagnosing-bugs | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Matt Pocock](https://github.com/mattpocock/skills/blob/main/skills/engineering/diagnosing-bugs/SKILL.md). |
| domain-modeling | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Matt Pocock](https://github.com/mattpocock/skills/blob/main/skills/engineering/domain-modeling/SKILL.md). |
| design-taste-frontend | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Upstream atual](https://github.com/Leonxlnx/taste-skill/blob/main/skills/taste-skill/SKILL.md). |
| ask-sonner | Não verificável | Há [site oficial do Sonner](https://sonner.emilkowal.ski), mas não foi localizada uma origem upstream para a skill em si nem versão local. |
| baseline-ui | Não verificável | Skill local alterada em 12/10/2026; não foi localizada uma origem upstream pública. |
| brandkit | Não verificável | Origem provável em [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill/blob/main/skills/brandkit/SKILL.md), mas há pequena diferença de tamanho e nenhum SHA/versão local. |
| caveman | Não verificável | Não foi localizada origem upstream correspondente; sem versão local. |
| codebase-design | Não verificável | [Upstream Matt Pocock](https://github.com/mattpocock/skills/blob/main/skills/engineering/codebase-design/SKILL.md) tem 98 linhas e a cópia local 114; sem SHA para distinguir fork/formatação de desatualização. |
| create-design-md | Não verificável | Origem em [ibelick/ui-skills](https://github.com/ibelick/ui-skills/blob/main/skills/create-design-md/SKILL.md); cópia local modificada, 254 linhas contra 216 upstream, sem pin de revisão. |
| fixing-accessibility | Não verificável | [Upstream ibelick/ui-skills](https://github.com/ibelick/ui-skills/blob/main/skills/fixing-accessibility/SKILL.md); cópia local modificada, 136 linhas contra 123, sem SHA. |
| fixing-metadata | Não verificável | Versão local 1.0.1 e licença MIT, mas sem origem upstream rastreável encontrada. |
| fixing-motion-performance | Não verificável | [Upstream ibelick/ui-skills](https://github.com/ibelick/ui-skills/blob/main/skills/fixing-motion-performance/SKILL.md); local 151 linhas contra 153 upstream, sem versão/SHA local para comprovar identidade. |
| full-output-enforcement | Não verificável | Fonte provável [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill/blob/main/skills/output-skill/SKILL.md); não foi validada igualdade integral nem encontrado pin local. |
| gpt-taste | Não verificável | Associada ao [índice upstream](https://github.com/Leonxlnx/taste-skill/blob/main/skills/llms.txt), mas o caminho esperado do SKILL.md não está disponível. |
| grilling | Não verificável | Não foi encontrada fonte upstream atual correspondente; o caminho esperado no repositório Matt Pocock retorna 404. |

## Skills locais I–Z

| Skill | Resultado | Evidência e fonte |
|---|---|---|
| image-to-code | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/image-to-code-skill/SKILL.md). |
| imagegen-frontend-mobile | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/imagegen-frontend-mobile/SKILL.md). |
| imagegen-frontend-web | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/imagegen-frontend-web/SKILL.md). |
| industrial-brutalist-ui | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/brutalist-skill/SKILL.md). |
| minimalist-ui | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/minimalist-skill/SKILL.md). |
| redesign-existing-projects | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/redesign-skill/SKILL.md). |
| stitch-design-taste | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Leonxlnx](https://github.com/Leonxlnx/taste-skill/blob/main/skills/stitch-skill/SKILL.md). |
| improve-animations | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Emil](https://github.com/emilkowalski/skills/blob/main/skills/improve-animations/SKILL.md). |
| mobile-native | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Emil](https://github.com/emilkowalski/skills/blob/main/skills/mobile-native/SKILL.md). |
| pick-ui-library | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Emil](https://github.com/emilkowalski/skills/blob/main/skills/pick-ui-library/SKILL.md). |
| review-animations | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Emil](https://github.com/emilkowalski/skills/blob/main/skills/review-animations/SKILL.md). |
| write-swift | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [Emil](https://github.com/emilkowalski/skills/blob/main/skills/write-swift/SKILL.md). |
| research | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Matt Pocock](https://github.com/mattpocock/skills/blob/main/skills/engineering/research/SKILL.md). |
| tdd | Sincronizada em 12/10/2026 | Conteúdo sincronizado em 12/10/2026 com a versão atual do upstream. [Matt Pocock](https://github.com/mattpocock/skills/blob/main/skills/engineering/tdd/SKILL.md). |
| to-issues | Sincronizada em 12/10/2026 | Atualizada a partir do upstream to-tickets; o nome local foi mantido por compatibilidade e a convenção HITL/AFK foi preservada. [ask-matt upstream](https://github.com/mattpocock/skills/blob/main/skills/engineering/ask-matt/SKILL.md). |
| to-prd | Sincronizada em 12/10/2026 | Atualizada a partir do upstream to-spec; o nome local foi mantido por compatibilidade. [Changelog](https://github.com/mattpocock/skills/blob/main/CHANGELOG.md) e [to-spec](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-spec/SKILL.md). |
| ui-skills-root | Parece atual | Comparação direta confirmou identidade com o upstream em 12/10/2026; nenhuma cópia necessária. [ibelick/ui-skills](https://github.com/ibelick/ui-skills/blob/main/skills/ui-skills-root/SKILL.md). |
| resolving-merge-conflicts | Parece atual | Os 5 passos locais correspondem ao [upstream](https://github.com/mattpocock/skills/blob/main/skills/engineering/resolving-merge-conflicts/SKILL.md); sem SHA local. |
| write-a-skill | Parece atual | Cópia local corresponde ao conjunto de skills atualmente visível em [Matt Pocock/skills](https://github.com/mattpocock/skills/tree/main/skills); sem SHA local. |
| zoom-out | Parece atual | Cópia local de 7 linhas corresponde ao [upstream](https://github.com/mattpocock/skills/blob/main/skills/engineering/zoom-out/SKILL.md); sem SHA local. |
| improve-ui | Não verificável | Skill local sem upstream público identificado. |
| process-meeting | Não verificável | Skill local sem upstream público identificado. |
| skill-router | Não verificável | Skill personalizada criada neste workspace; sem upstream. |
| transcrever-reuniao | Não verificável | Skill local sem upstream público identificado. |
| prototype | Não verificável | Há skills homônimas em repositórios diferentes, incluindo [Emil](https://github.com/emilkowalski/skills/blob/main/skills/prototype/SKILL.md); sem pin local para determinar a origem exata. |

## Skills de sistema e plugins

A versão abaixo é a versão do pacote/cache que contém a skill, não necessariamente uma versão independente da skill.

| Skill | Versão local | Resultado e fonte |
|---|---:|---|
| imagegen | Sem versão | Upstream público em [openai/skills](https://github.com/openai/skills/blob/main/skills/.system/imagegen/SKILL.md); instalação local sem versão/commit para comparação. |
| openai-docs | Sem versão | Upstream público em [openai/skills](https://github.com/openai/skills/blob/main/skills/.system/openai-docs/SKILL.md); instalação local sem versão/commit. |
| skill-creator | Sem versão | Upstream público em [openai/skills](https://github.com/openai/skills/blob/main/skills/.system/skill-creator/SKILL.md); instalação local sem versão/commit. |
| skill-installer | Sem versão | Upstream público em [openai/skills](https://github.com/openai/skills/blob/main/skills/.system/skill-installer/SKILL.md); instalação local sem versão/commit. |
| computer-use:computer-use | 26.1007.21434 | Manifesto aponta para [este caminho](https://github.com/openai/openai/tree/master/project/cua/sky_js/plugin), que não ficou acessível para comparação. |
| visualize:visualize | 1.0.49 | Manifesto local fornece homepage OpenAI, mas não repositório público upstream para comparação. |
| plugin-management:plugin-management | 0.1.0 | Manifesto aponta para [este caminho](https://github.com/openai/openai/tree/master/chatgpt/oai-maintained-plugins/plugins/plugin-management), inacessível na consulta. |
| sites:sites | 1.0.0 | Manifesto local não fornece repositório upstream rastreável. |
| work-pets:create-pet | 0.1.6 | Versão compartilhada do pacote work-pets; [caminho oficial indicado](https://github.com/openai/openai/tree/master/chatgpt/oai-maintained-plugins/plugins/pets) inacessível. |
| work-pets:pets | 0.1.6 | Mesmo pacote e limitação de comparação de create-pet. |
| work-pets:update-pet | 0.1.6 | Mesmo pacote e limitação de comparação de create-pet. |
| documents:documents | 26.1007.11041 | Versão Primary Runtime. [Issue oficial](https://github.com/openai/codex/issues/51340) mostra essa como a versão mais recente observada em 09/10/2026; não foi possível confirmar se continuava atual em 12/10. |
| pdf:pdf | 26.1007.11041 | Mesmo pacote e limitação de comparação de documents. |
| presentations:Presentations | 26.1007.11041 | Mesmo pacote e limitação de comparação de documents. |
| template-creator:template-creator | 26.1007.11041 | Mesmo pacote e limitação de comparação de documents. |
| spreadsheets:Spreadsheets | 26.1007.11041 | Mesmo pacote e limitação de comparação de documents. |
| spreadsheets:excel-live-control | 26.1007.11041 | Mesmo pacote e limitação de comparação de documents. |

## Limitações

O commit local 03c1fb8, datado de 22/09/2026, registra a publicação no repositório pessoal MySkills; ele não fixa a revisão upstream de cada skill. Em geral, “parece atual” indica comparação de conteúdo com uma página main acessível, não comparação por SHA. Não executei as skills para testar seu comportamento; a auditoria verifica origem e divergência visível, não qualidade funcional.

Para os pacotes Primary Runtime, o endpoint oficial de atualização não pôde ser consultado: https://persistent.oaistatic.com/codex-primary-runtime/latest/win32-x64/LATEST.json. Portanto, 26.1007.11041 é a versão mais recente que encontrei documentada em 09/10, mas sua vigência em 12/10 permanece não verificável.
