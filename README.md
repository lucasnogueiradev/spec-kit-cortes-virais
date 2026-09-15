# 🎬 Spec-Kit: Cortes Virais (Video Worker)

O **Spec-Kit Cortes Virais** é um laboratório prático projetado para ensinar **Spec-Driven Development (SDD)**. Neste ambiente, em vez de programar no chute ("vibe coding"), você aprenderá a guiar Inteligências Artificiais (como Cursor, Claude Code, ou ChatGPT) através de especificações rigorosas.

## 🎯 O Desafio
O objetivo deste laboratório é construir um microsserviço assíncrono em **Python (FastAPI)** resiliente. 
Este sistema é capaz de:
1. Baixar vídeos longos do YouTube (`yt-dlp`).
2. Transcrever o áudio localmente (`faster-whisper`).
3. Fatiar a transcrição e pedir para a IA (`Google Gemini Flash`) identificar os melhores ganchos e cortes virais.
4. Renderizar o vídeo em formato vertical 9:16 com legendas animadas em karaokê (`FFmpeg`).

> **💡 Dica de Ouro:** Toda a arquitetura foi desenhada para rodar em **computadores locais (CPU)**, sem exigir placa de vídeo dedicada, usando um sistema inteligente de *Checkpoints* (se a luz cair, ele volta de onde parou).

## 🚀 Como Usar

### 1. Preparação da IA
Copie o conteúdo do arquivo `SKILL.md` e cole como a primeira instrução para a sua IA (ou no "System Prompt"). Isso fará com que ela assuma a persona de um tutor rigoroso de SDD.

### 2. O Método Educaflex
Em seguida, navegue pela pasta `.spec/`.
Primeiro, a IA deve ler a `.spec/constituicao.md` (As regras inquebráveis do projeto).

Depois, construa o projeto módulo por módulo. Para cada pasta dentro de `.spec/features/`:
- **spec.md**: Explica a regra de negócio (O *que* fazer).
- **tasks.md**: O passo a passo técnico de execução (O *como* fazer).

Peça para a IA: *"Leia o spec e as tasks da feature 01 e implemente o código."* 
Só passe para a feature 02 quando a 01 estiver 100% concluída.

## ⚖️ Licença
Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
