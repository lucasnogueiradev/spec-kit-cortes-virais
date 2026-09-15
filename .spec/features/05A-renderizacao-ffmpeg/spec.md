# US-005: Renderizador de Vídeo 9:16 com Legenda Dinâmica

**Como** publicadora em redes sociais (TikTok, Reels),  
**Eu quero** transformar os cortes selecionados (que estão na horizontal 16:9) em vídeos verticais 9:16 com título colorido no topo e legenda estilo karaokê no centro,  
**Para que** eles estejam 100% prontos para viralizar sem eu precisar abrir um editor de vídeo.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: O renderizador precisa gerar um arquivo `.ass` temporário formatando a legenda animada (a palavra do momento em cor viva, e o resto da frase branca translúcida).
- **AC-002**: O renderizador deve invocar o binário do `ffmpeg` com filtros complexos (crop 9:16 + drawbox + drawtext).
- **AC-003**: O arquivo final deve ser um arquivo MP4 salvo na pasta `outputs/`.
- **AC-004**: Toda a operação deve ser tratada como Background Task no FastAPI, para o frontend poder consultar o progresso.
