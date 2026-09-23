# Minhas skills para o Codex

Catálogo público das skills que uso no Codex, organizado por finalidade e com exemplos de combinação para diferentes tipos de trabalho.

Este repositório reúne **56 skills pessoais**. A pasta `.system/` também contém seis skills internas distribuídas com o Codex; elas aparecem neste guia apenas para deixar a origem do conjunto completo transparente e podem ser omitidas em uma publicação pública.

Uma skill não é necessariamente um programa ou uma ferramenta nova. Na maioria dos casos, é um conjunto de instruções que ensina o Codex a executar uma tarefa seguindo determinado método. Algumas também incluem scripts, modelos e materiais de referência.

## O que está aqui

As skills estão organizadas por finalidade. Algumas cumprem papéis semelhantes e **não precisam ser utilizadas simultaneamente**.

## Sumário rápido

| Parte | Assunto | Quantidade |
|---|---|---:|
| 1 | Como usar as skills no Codex | Orientações |
| 2 | Planejamento, especificações e organização | 14 |
| 3 | Programação, arquitetura, debugging e testes | 11 |
| 4 | Design de interfaces e identidade visual | 12 |
| 5 | Protótipos, imagens e bibliotecas frontend | 7 |
| 6 | Animações e microinterações | 6 |
| 7 | Reuniões, criação de skills e preferências de resposta | 6 |
| 8 | Skills internas do Codex | 6 |
| 9 | Onde guardar e organizar as skills no Windows | Caminhos e comando |
| 10 | Escolher o que você vai fazer | 5 fluxos práticos |
| **Total** | **Conjunto completo (incluindo `.system`)** | **62** |

# 1. Como usar suas skills no Codex

No Codex do VS Code, você pode pedir que ele escolha uma skill automaticamente pela descrição da tarefa ou chamá-la explicitamente com `$nome-da-skill`. O seletor `/skills` também ajuda a encontrá-las.

**Exemplo de prompt para o Codex:**

```text
$diagnose Investigue por que minha aplicação está fazendo requisições
duplicadas à API. Reproduza o problema, encontre a causa e crie um
teste de regressão.
```

**Atenção aos nomes:** algumas pastas possuem nomes diferentes dos nomes declarados para invocação. Por exemplo, a pasta `taste-skill` declara `design-taste-frontend` e a pasta `soft-skill` declara `high-end-visual-design`. Nos exemplos abaixo, o nome indicado em código é o nome apropriado para chamar a skill; o nome da pasta aparece entre parênteses quando for diferente.

Também existem skills configuradas para execução manual, como `handoff`, `prototype`, `wayfinder` e `implement`. Nessas, vale usar o nome explicitamente, em vez de esperar que o Codex decida ativá-las.

> **Como escolher:** comece pela tarefa que pretende realizar, não por quantas skills consegue ativar. Uma skill de planejamento, uma de implementação e uma de revisão costumam cobrir bem um fluxo de trabalho.

# 2. Planejamento, especificações e organização — 14 skills

**Onde usar:** Codex com a pasta do projeto aberta, preferencialmente com Git e documentação do projeto.

| Skill | Para que serve e quando usar |
|---|---|
| `ask-matt` | Um orientador das outras skills de engenharia. Quando você sabe o que quer fazer, mas não sabe qual workflow escolher. |
| `grilling` | Entrevista você para encontrar lacunas, requisitos e decisões não resolvidas antes de começar o desenvolvimento. |
| `grill-me` | Versão de entrada para uma entrevista rigorosa sobre determinada ideia ou plano. |
| `grill-with-docs` | Faz a entrevista e registra as decisões em documentos, incluindo ADRs (registros de decisões arquiteturais) e glossário. |
| `zoom-out` | Pede ao Codex que amplie a perspectiva e explique como um módulo ou problema se encaixa na arquitetura geral. |
| `wayfinder` | Planeja projetos grandes demais para serem concluídos em uma única sessão. Produz um mapa de decisões e tarefas. |
| `domain-modeling` | Define conceitos, relacionamentos e termos do domínio, evitando ambiguidades entre regras de negócio e código. |
| `to-prd` | Transforma a conversa em um PRD, documento que descreve o problema, a solução e os requisitos do produto. |
| `to-spec` | Transforma o que já foi discutido em uma especificação para implementação, sem iniciar uma nova entrevista. |
| `to-issues` | Divide um plano em issues independentes e verificáveis no gerenciador de tarefas do projeto. |
| `to-tickets` | Cria tickets pequenos, com suas dependências, para que agentes consigam implementar partes do projeto separadamente. |
| `triage` | Classifica issues, verifica se estão suficientemente detalhadas e prepara instruções para agentes ou desenvolvedores. |
| `setup-matt-pocock-skills` | Configura o repositório para utilizar o conjunto de skills de engenharia, incluindo gerenciador de issues e documentação. |
| `handoff` | Produz um documento de transferência de contexto para outro agente ou uma nova sessão do Codex. |

## Caso de uso prático: começar um aplicativo

Imagine que você está começando um aplicativo e tem apenas a ideia e algumas telas em mente. Um fluxo completo poderia ser:

1. **`grill-with-docs`:** entender e documentar a ideia.
2. **`domain-modeling`:** definir os conceitos de negócio.
3. **`to-prd`:** formalizar o produto.
4. **`to-tickets`:** criar tarefas com dependências.
5. **`implement`:** desenvolver cada tarefa.

**Nota:** para um projeto pequeno, você não precisa passar por todas essas etapas. `grill-me` seguido de `to-spec` e `implement` pode ser suficiente. Para um projeto grande, `wayfinder` e `to-tickets` ajudam a manter o trabalho organizado por várias sessões.

# 3. Programação, arquitetura, debugging e testes — 11 skills

**Onde usar:** principalmente no Codex do VS Code ou no terminal, com acesso ao código-fonte, Git e ferramentas de compilação.

| Skill | Para que serve e quando usar |
|---|---|
| `codebase-design` | Projeta módulos com interfaces pequenas e responsabilidades bem definidas. Útil antes de criar ou reorganizar o núcleo de um sistema. |
| `improve-codebase-architecture` | Inspeciona o código existente, identifica oportunidades de refatoração e apresenta um relatório visual em HTML. |
| `tdd` | Implementa funcionalidades seguindo testes primeiro, depois código e refatoração. Útil para regras de negócio e integrações. |
| `diagnose` | Investiga bugs difíceis ou problemas de desempenho reproduzindo o erro, testando hipóteses e verificando a correção. |
| `diagnosing-bugs` | Uma variante bastante semelhante de `diagnose`, também centrada em criar uma forma confiável de reproduzir e medir o problema. |
| `code-review` | Compara alterações com um commit ou branch e verifica padrões do projeto e conformidade com a especificação. |
| `implement` | Implementa uma especificação ou tickets, executa testes e revisão e prevê um commit ao concluir. |
| `research` | Pesquisa informações técnicas em fontes primárias, como documentação oficial, e registra os resultados em Markdown. |
| `resolving-merge-conflicts` | Analisa e resolve conflitos de Git, preservando a intenção das alterações e executando as verificações necessárias. |
| `teach` | Cria um ambiente de aprendizado progressivo, com exercícios, registros e materiais de referência. |
| `write-swift` | Orienta o desenvolvimento moderno em Swift, com ênfase em modelagem, segurança de concorrência e boas práticas da linguagem. |

## Exemplo: desenvolvimento em C#

Para um aplicativo que precisa consumir pouca memória, você pode começar com `codebase-design` para definir os módulos e as interfaces. Em seguida, usar `tdd` para desenvolver as operações críticas e `diagnose` caso o consumo de memória fique acima do esperado.

**Prompt para copiar no Codex:**

```text
$codebase-design Analise a arquitetura do meu projeto C# NativeAOT.
Proponha módulos com interfaces pequenas, baixo acoplamento e baixo
consumo de memória. Não altere o código ainda.
```

**Minha sugestão de organização:** use `diagnose` como sua skill habitual de debugging e deixe `diagnosing-bugs` como alternativa, em vez de carregar ambas na mesma tarefa. A skill `implement` merece um cuidado especial: suas instruções incluem criar um commit. Se você quiser apenas uma alteração experimental, declare isso no pedido antes de começar.

# 4. Design de interfaces e identidade visual — 12 skills

**Onde usar:** desenvolvimento frontend, criação de landing pages, dashboards, design systems e identidade visual. O nome entre parênteses é a pasta no ZIP, quando diferente do nome da skill.

| Skill | Para que serve e quando usar |
|---|---|
| `hallmark` | Skill abrangente de design para criar, analisar e redesenhar páginas, componentes e aplicativos, combatendo layouts genéricos. |
| `design-taste-frontend` (`taste-skill`) | Cria interfaces frontend com direção visual própria, ajustando densidade, criatividade e movimento ao projeto. |
| `design-taste-frontend-v1` (`taste-skill-v1`) | Versão anterior da skill de design, útil para manter consistência em projetos feitos com suas regras originais. |
| `gpt-taste` (`gpt-tasteskill`) | Cria páginas visuais mais experimentais, com tipografia editorial, layouts variados e animações avançadas com GSAP. |
| `high-end-visual-design` (`soft-skill`) | Aplica um estilo visual sofisticado, com espaçamento, tipografia, sombras e composição cuidadosamente definidos. |
| `minimalist-ui` (`minimalist-skill`) | Cria interfaces minimalistas e editoriais, com cores discretas, tipografia marcante e poucos efeitos. |
| `industrial-brutalist-ui` (`brutalist-skill`) | Cria interfaces de estética industrial e brutalista, com grades rígidas, tipografia extrema e aparência de terminal. |
| `redesign-existing-projects` (`redesign-skill`) | Audita e moderniza um site ou aplicativo existente sem recriar tudo nem alterar desnecessariamente suas funcionalidades. |
| `emil-design-eng` | Aplica princípios de engenharia de design para melhorar componentes, interações e os detalhes visuais de uma interface. |
| `apple-design` | Traduz princípios de interfaces fluidas da Apple para aplicações web, incluindo gestos, movimento e molas físicas. |
| `brandkit` | Cria propostas visuais de identidade de marca, incluindo logotipos, paletas, aplicações e apresentações de marca. |
| `stitch-design-taste` (`stitch-skill`) | Gera um `DESIGN.md` para orientar a criação consistente de telas no Google Stitch. |

## Escolhendo um estilo visual

As referências visuais da explicação original representam quatro caminhos de design:

| Estilo | Skill principal | Onde combina melhor |
|---|---|---|
| **Minimalista** | `minimalist-ui` | Dashboards administrativos, produtividade e ferramentas com leitura intensa. |
| **Sofisticado** | `high-end-visual-design` | Aplicações empresariais que precisam de aparência refinada. |
| **Brutalista** | `industrial-brutalist-ui` | Portfólios, interfaces experimentais e painéis de estética industrial. |
| **Experimental** | `gpt-taste` | Landing pages de alto impacto e experiências visuais com animação. |

*As imagens mostradas na versão interativa eram referências ilustrativas dos estilos, não resultados produzidos pelas skills.*

**Nota de combinação:** para a maioria dos projetos web, eu começaria escolhendo apenas uma entre `hallmark`, `design-taste-frontend` e `redesign-existing-projects`, conforme esteja criando algo novo ou modificando algo existente. Depois utilizaria `apple-design` ou `emil-design-eng` para aperfeiçoar interações específicas, sem misturar diversas skills que impõem estilos diferentes.

# 5. Protótipos, imagens e bibliotecas frontend — 7 skills

| Skill | Para que serve e quando usar |
|---|---|
| `image-to-code` (`image-to-code-skill`) | Cria referências visuais de um site e depois implementa o frontend para reproduzir o design. |
| `imagegen-frontend-web` | Produz conceitos visuais de páginas web, com uma imagem independente para cada seção. |
| `imagegen-frontend-mobile` | Produz telas conceituais de aplicativos móveis, como onboarding, dashboard, configurações e navegação. Não gera o aplicativo funcional. |
| `prototype` | Constrói várias versões realmente diferentes de um componente para você comparar visualmente antes de escolher. |
| `pick-ui-library` | Seleciona bibliotecas frontend adequadas à tarefa, considerando também as dependências existentes. |
| `mobile-native` | Ajusta uma aplicação web para parecer e se comportar como um aplicativo nativo no celular. |
| `ask-sonner` | Especializada na biblioteca Sonner para notificações toast em React: instalação, estilo, eventos e correção de problemas. |

## Uma combinação especialmente útil: criar um drawer

Para criar um drawer com várias possibilidades de layout, você poderia usar `prototype` para construir três versões:

- **Compacto:** painel lateral estreito, com informações essenciais e ações rápidas.
- **Expandido:** painel lateral largo, com detalhes, campos e histórico disponíveis sem navegação adicional.
- **Painel dividido:** duas colunas ou áreas internas, por exemplo detalhes à esquerda e linha do tempo à direita.

Depois de escolher o layout, utilize `pick-ui-library` para identificar os componentes e bibliotecas adequados.

**Qual skill de imagem escolher?** Use `imagegen-frontend-web` quando a prioridade for explorar uma direção visual antes de programar. Use `image-to-code` quando quiser que o Codex execute também a implementação a partir dessa direção visual. Para aplicativos Android ou iOS, `imagegen-frontend-mobile` é a opção voltada à concepção das telas.

# 6. Animações e microinterações — 6 skills

| Skill | Para que serve e quando usar |
|---|---|
| `animation-vocabulary` | Identifica o nome técnico de um efeito que você descreve informalmente. |
| `find-animation-opportunities` | Analisa a interface e propõe onde animações realmente acrescentariam valor, sem implementar alterações. |
| `animate` | Implementa animações para a web, escolhendo propriedades, curvas e duração conforme a interação. |
| `animate-expo` | Implementa animações para React Native e Expo, considerando desempenho e execução na UI thread. |
| `review-animations` | Revisa animações existentes ou alterações recentes, procurando problemas de fluidez, comportamento e qualidade. |
| `improve-animations` | Audita animações de um projeto inteiro e produz planos detalhados para melhorar as que precisam de ajustes. |

## Exemplos de microinterações

A demonstração original incluía três animações interativas. Elas ficam descritas assim:

| Animação | Comportamento | Exemplo de uso |
|---|---|---|
| **Pop-in** | O elemento cresce levemente e volta ao tamanho normal, com uma entrada elástica. | Confirmação de uma ação ou chegada de um pequeno componente. |
| **Slide-up** | Um painel desliza para cima, geralmente com transição suave e desaceleração. | Abertura de sheet, drawer ou detalhes contextuais. |
| **Stagger** | Elementos semelhantes aparecem um após o outro, com pequeno intervalo. | Carregamento de listas, cartões e linhas de informação. |

**Fluxo sugerido:** `find-animation-opportunities` → `animate` → `review-animations`. Quando o projeto já tem dezenas de animações e precisa de revisão abrangente, substitua a primeira etapa por `improve-animations`.

**Acessibilidade:** em qualquer desses efeitos, considere as preferências de movimento reduzido do usuário e evite animação decorativa que atrapalhe tarefas frequentes.

# 7. Reuniões, criação de skills e preferências de resposta — 6 skills

| Skill | Para que serve e quando usar |
|---|---|
| `process-meeting` | Transforma reuniões, vídeos ou transcrições em documentação contínua do projeto, incluindo decisões, pendências, glossário e evidências. |
| `transcrever-reuniao` | Utiliza Whisper para transcrever um vídeo de reunião e gerar um relatório Markdown, com resumo, decisões e tarefas. |
| `write-a-skill` | Ajuda a escrever uma skill nova, estruturando o `SKILL.md`, referências e scripts. |
| `writing-great-skills` | Serve como guia para melhorar skills existentes, tornando suas instruções mais previsíveis e seus gatilhos mais claros. |
| `caveman` | Faz o agente responder de maneira extremamente curta e direta, reduzindo explicações e texto desnecessário. |
| `full-output-enforcement` (`output-skill`) | Orienta o agente a entregar arquivos completos, sem substituir trechos por comentários como `// restante do código`. |

A `process-meeting` é especialmente interessante para reuniões recorrentes, pois mantém um histórico contínuo de decisões e informações. A `transcrever-reuniao` é mais direta quando você precisa transformar uma gravação em texto e gerar um relatório.

> **Atenção à configuração local:** a sua `transcrever-reuniao` contém caminhos absolutos de instalação do Faster-Whisper e de saída dos arquivos na unidade `D:`, além de uma configuração para CUDA. Isso significa que ela depende da estrutura de pastas e do ambiente de execução descritos no próprio arquivo. Para utilizar em outra máquina, será necessário adaptar esses caminhos e verificar os requisitos de GPU.

# 8. Skills internas do Codex — 6 skills

Estas aparecem dentro da pasta `.system` no ZIP. Elas são voltadas a capacidades gerais e manutenção do próprio ambiente.

| Skill | Para que serve e quando usar |
|---|---|
| `imagegen` | Gera e edita imagens, ilustrações, mockups e recursos visuais para os projetos, utilizando a ferramenta de imagem disponível ou, em casos específicos, uma CLI com API. |
| `openai-docs` | Consulta documentação oficial e atualizada da OpenAI para APIs, modelos, preços, Codex e configurações. |
| `plugin-creator` | Cria a estrutura e os manifestos de novos plugins para o Codex, com validação e arquivos de distribuição. |
| `review-agent` | Realiza revisão técnica somente de leitura, procurando defeitos concretos em alterações de código. |
| `skill-creator` | Cria ou atualiza skills com instruções, referências e scripts quando necessários, incluindo validação da estrutura. |
| `skill-installer` | Instala skills de coleções disponibilizadas pela OpenAI ou de repositórios GitHub. |

**Nota:** eu manteria essas seis sob o gerenciamento do próprio Codex. Não é necessário copiá-las para cada projeto. As skills internas disponíveis podem variar conforme a instalação e a versão.

# 9. Onde guardar e organizar as skills no Windows

Você pode separar as skills pessoais, disponíveis para vários projetos, das específicas de cada repositório.

## Skills pessoais

**Disponíveis em vários projetos:**

```text
%USERPROFILE%\.agents\skills\
```

Eu colocaria aqui `diagnose`, `tdd`, `codebase-design`, `handoff`, `research` e as skills de design que você usa frequentemente.

## Skills de um projeto

**Disponíveis dentro do repositório:**

```text
SEU_PROJETO\.agents\skills\
```

Aqui você pode criar skills próprias que descrevem uma API específica, suas regras de negócio, padrões de testes ou procedimentos de implantação.

## Instalações existentes

Se você instalou suas skills em `~/.codex/skills`, não precisa movê-las sem antes verificar se sua instalação atual já as reconhece. O ZIP mostra as pastas relativas, mas não confirma o caminho original de cada uma.

Para descobrir os caminhos reais na sua máquina, execute no PowerShell:

```powershell
$roots = @(
    "$HOME\.agents\skills",
    "$HOME\.codex\skills",
    "$PWD\.agents\skills"
)

foreach ($root in $roots) {
    if (Test-Path $root) {
        Write-Host "`nSkills em: $root"
        Get-ChildItem $root -Filter SKILL.md -Recurse -File |
            Select-Object -ExpandProperty FullName
    }
}
```

**Nota sobre muitas skills:** o Codex pode reduzir algumas descrições da lista inicial para economizar contexto. Isso não significa que o conteúdo completo tenha sido perdido. Você pode manter as skills pessoais mais utilizadas e deixar as específicas dentro de cada projeto.

# 10. Escolha o que você vai fazer

Esta seção corresponde ao seletor interativo da explicação original. Os cinco caminhos aparecem abaixo com sequência de skills e prompt pronto para copiar.

## Opção A — Começar um aplicativo novo

**Sequência:** `grill-with-docs` → `to-spec` → `prototype` → `design-taste-frontend` → `tdd` → `code-review`

**Quando escolher:** você tem uma ideia de produto, mas ainda precisa consolidar requisitos, testar possibilidades visuais e implementar o primeiro fluxo.

```text
Estou começando um aplicativo novo. Use $grill-with-docs para definir
os requisitos e documentar as decisões. Depois, use $to-spec para
preparar uma especificação de implementação.
```

## Opção B — Corrigir um bug difícil

**Sequência:** `diagnose` → `tdd` → `code-review`

**Quando escolher:** o problema aparece de modo intermitente, envolve desempenho, integração ou exige uma maneira objetiva de comprovar que foi corrigido.

```text
Use $diagnose para reproduzir o erro e identificar a causa. Corrija-o,
crie um teste de regressão usando $tdd e revise as alterações com
$code-review em relação à branch main.
```

## Opção C — Melhorar uma interface existente

**Sequência:** `redesign-existing-projects` → `prototype` → `find-animation-opportunities` → `animate` → `review-animations`

**Quando escolher:** a aplicação já funciona, mas a aparência, o layout ou as transições precisam de aprimoramento sem reescrever as regras de negócio.

```text
Use $redesign-existing-projects para auditar a interface atual,
preservando a funcionalidade. Proponha alternativas com $prototype
antes de implementar mudanças visuais significativas.
```

## Opção D — Criar software leve em C#

**Sequência:** `codebase-design` → `research` → `tdd` → `implement` → `code-review`

**Quando escolher:** consumo de memória, inicialização rápida e separação entre núcleo de processamento e interface são prioridades.

```text
Use $codebase-design para propor uma arquitetura em C# com baixo
consumo de memória. Utilize $research para investigar pontos técnicos
que dependem de documentação oficial e $tdd para desenvolver os
módulos críticos.
```

## Opção E — Organizar um projeto grande

**Sequência:** `setup-matt-pocock-skills` → `wayfinder` → `to-tickets` → `implement` → `handoff`

**Quando escolher:** o escopo envolve muitas decisões e tarefas, possivelmente distribuídas entre várias sessões ou agentes.

```text
Use $setup-matt-pocock-skills para configurar o repositório. Em
seguida, use $wayfinder para mapear o trabalho e $to-tickets para
criar tarefas pequenas, com dependências claras.
```

## Exemplo: criar uma skill específica de API

Para um projeto que consome uma API importante, eu criaria também uma skill específica. Ela poderia documentar os endpoints validados, a estrutura dos dados, o tratamento de erros, as regras de cache e os limites de requisições. Assim, o Codex não precisaria redescobrir essas decisões a cada sessão.

Um caminho possível seria:

```text
SEU_PROJETO\.agents\skills\api\SKILL.md
```

Crie a estrutura com `$skill-creator` e utilize a nova skill junto com `diagnose`, `tdd` ou `implement`, conforme a tarefa.

**Cuidados finais:** revise as ações previstas antes de invocar skills que escrevem no Git ou em ferramentas externas. `to-issues` e `to-tickets` podem publicar tarefas no gerenciador configurado; `implement` inclui um commit; já `code-review` é apropriada quando você quer apenas inspecionar alterações. Manter uma cópia dos documentos de arquitetura e especificações no repositório também torna o `handoff` mais compacto e confiável.

---

**Resumo de uso:** comece com a necessidade real, selecione poucas skills complementares e mantenha os documentos e decisões importantes próximos ao código. O conjunto é uma caixa de ferramentas: o ganho está em escolher a ferramenta adequada, não em ativar todas ao mesmo tempo.
