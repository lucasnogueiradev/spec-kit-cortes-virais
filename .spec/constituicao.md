# 📜 Constituição do Projeto: Video Worker (Educaflex)

Este arquivo define a espinha dorsal técnica e as regras inquebráveis do projeto "Video Worker" (Gerador automático de Cortes Virais de Vídeos Longos). 

## 1. Stack Tecnológica Base
- **Linguagem**: Python 3.10+
- **Backend**: `fastapi` e `uvicorn` (A API para interagir e ver status)
- **Downloader**: `yt-dlp` via chamadas de sistema (subprocess)
- **IA de Áudio**: `faster-whisper` configurado OBRIGATORIAMENTE para rodar em CPU (`device="cpu", compute_type="int8"`).
- **IA de Curadoria**: Google Gemini Flash via API REST (`requests`).

---

## 2. A Grande Escolha: Como Renderizar o Vídeo?
O projeto possui duas abordagens para renderizar o vídeo final. A aluna deve escolher **apenas uma** (Feature 05A ou Feature 05B) de acordo com o hardware do seu PC e seu conhecimento prévio.

### Opção A: Motor Raiz (FFmpeg) - *Feature 05A*
O FFmpeg usa o terminal para "queimar" as legendas (`.ass`) no vídeo.
* **Requisito Mínimo de PC**: 4GB de RAM, Processador i3/Ryzen 3.
* **Vantagens**: Extremamente rápido, usa menos memória, roda tudo no backend sem precisar de frontend.
* **Desvantagens**: Edição rígida. Para trocar a fonte, mudar a cor ou fazer o texto "pular", você precisa mexer na matemática complexa do código Python.

### Opção B: Motor Visual (Remotion Studio) - *Feature 05B*
O backend Python não renderiza o vídeo. Ele salva um arquivo `JSON` com os dados do corte, e o "Remotion" (um projeto em React/Node.js) lê esse JSON e cria o vídeo usando HTML e CSS.
* **Requisito Mínimo de PC**: 8GB de RAM, Processador i5/Ryzen 5 (O Remotion abre navegadores invisíveis para gravar o vídeo, o que consome bastante RAM).
* **Vantagens**: Poder total de design. Você usa CSS para fazer sombras, fontes neon, importar do Google Fonts e criar animações complexas estilo TikTok com 1 linha de código. Você pode dar "Play" no navegador antes de exportar.
* **Desvantagens**: Mais pesado e mais lento. Exige conhecimento básico de JavaScript/React/CSS.

---

## 3. Princípios de Arquitetura (Resiliência Educacional)
- **Zero Bancos de Dados Complexos**: Para facilitar a vida das alunas, os jobs serão salvos num arquivo `jobs.json` local.
- **Checkpoints (Early Return)**: Se a internet cair, o sistema nunca começa do zero. Ele verifica se o `video.mp4` ou o `transcript.json` já existem.
- **Chunking (Fatiamento)**: A IA não vai ler o vídeo de 6 horas de uma vez. Ela vai ler fatias de 30 minutos para não travar a API do Gemini.
