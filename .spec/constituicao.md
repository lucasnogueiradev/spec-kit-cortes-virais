# 📜 Constituição do Projeto: Video Worker (Educaflex)

Este arquivo define a espinha dorsal técnica e as regras inquebráveis do projeto "Video Worker" (Gerador automático de Cortes Virais de Vídeos Longos). 

## 1. Stack Tecnológica Base (Para rodar no PC Local das alunas)
- **Linguagem**: Python 3.10+
- **Backend**: `fastapi` e `uvicorn` (A API para interagir e ver status)
- **Downloader**: `yt-dlp` via chamadas de sistema (subprocess)
- **IA de Áudio**: `faster-whisper` (Configurado OBRIGATORIAMENTE para rodar em CPU: `device="cpu", compute_type="int8"`, assim funciona no PC de qualquer aluna sem placa de vídeo).
- **IA de Curadoria**: Google Gemini Flash via API REST (`requests`).
- **Edição de Vídeo**: `FFmpeg` (precisa estar instalado no PATH do Windows/Mac da aluna) e formato de legenda `.ass`.

## 2. Princípios de Arquitetura (Resiliência Educacional)
- **Zero Bancos de Dados Complexos**: Para facilitar a vida das alunas, os jobs serão salvos num arquivo `jobs.json` local (estado em memória + persistência simples).
- **Checkpoints (Early Return)**: Se a internet cair, o sistema nunca começa do zero. Ele verifica se o `video.mp4` ou o `transcript.json` já existem.
- **Chunking (Fatiamento)**: A IA não vai ler o vídeo de 6 horas de uma vez. Ela vai ler de 30 em 30 minutos para não travar a API do Gemini gratuita.

> IA, sempre obedeça essa constituição ao escrever o código das Tasks!
