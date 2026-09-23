---
name: transcrever-reuniao
description: Transcreve um vídeo de reunião usando Whisper e gera um relatório detalhado em markdown (.md) com resumo executivo, decisões, pendências e participantes. Use quando o usuário fornecer um caminho de vídeo e quiser transcrever ou documentar uma reunião, ou mencionar "transcrever", "reunião", "gerar relatório de reunião", "whisper".
---

# Transcrever Reunião

## Quick start

O usuário fornece o caminho do vídeo. Você transcreve e gera o `.md`.

```
Transcreva o vídeo em `C:\caminho\para\MinhaReuniao.mp4`.
```

## Workflow

### 1. Receber o caminho do vídeo

- Se o usuário não forneceu, pergunte: *"Qual o caminho completo do vídeo da reunião?"*
- O caminho vai substituir a variável `VIDEO_PATH` no comando abaixo.

### 2. Executar o Whisper

Execute no terminal (PowerShell):

```powershell
$env:WHISPER_EXE = "C:\caminho\para\faster-whisper-xxl.exe"
$env:TRANSCRIPT_OUTPUT_DIR = "C:\caminho\para\Legendas"
$env:WHISPER_MODEL_DIR = "C:\caminho\para\whispermodels"

& $env:WHISPER_EXE `
  --output_dir $env:TRANSCRIPT_OUTPUT_DIR `
  --output_format srt `
  --verbose True `
  --beep_off `
  --model large-v3-turbo `
  --model_dir $env:WHISPER_MODEL_DIR `
  --language pt `
  --device cuda `
  -ct float16 `
  "VIDEO_PATH"
```

- Use `mode=sync` com timeout de 600000ms (10 min).
- O SRT gerado fica em: `$env:TRANSCRIPT_OUTPUT_DIR\<nome-do-video>.srt`

### 3. Ler o SRT gerado

- Derive o nome do SRT a partir do nome do arquivo de vídeo (sem extensão + `.srt`).
- Leia o conteúdo completo do arquivo SRT gerado.

### 4. Analisar a transcrição

Com base no conteúdo do SRT, identifique:
- **Participantes** — nomes mencionados explicitamente ou vozes identificáveis pelo contexto
- **Assunto principal** — tema central da reunião
- **Decisões fechadas** — itens onde o grupo chegou a consenso
- **Pendências e próximas ações** — tarefas atribuídas ou itens em aberto
- **Pontos de atenção** — riscos, alertas, dependências mencionadas

### 5. Gerar o relatório `.md`

Siga o **template** em [REPORT_TEMPLATE.md](REPORT_TEMPLATE.md).

- Salve o arquivo no mesmo diretório do workspace do projeto, dentro de uma pasta com o nome do tema da reunião se fizer sentido, ou na raiz.
- Nome sugerido para o arquivo: `relatorio-reuniao-<tema>.md` (slug em minúsculas, sem acentos, palavras separadas por `-`).
- Data de geração: data atual no formato `DD/MM/AAAA`.

---

## Notas

- O Whisper usa GPU (CUDA). Se falhar por falta de VRAM, o erro aparece no terminal — avise o usuário.
- Se o SRT já existir (transcrição anterior), pergunte se quer usar o existente ou re-transcrever.
- Nunca inclua timestamps do SRT no relatório — só o conteúdo semântico.
