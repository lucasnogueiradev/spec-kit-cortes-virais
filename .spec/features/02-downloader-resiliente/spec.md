# US-002: Downloader Resiliente de YouTube

**Como** estudante de edição automatizada,  
**Eu quero** que o sistema baixe vídeos do YouTube automaticamente,  
**Para que** eu possa processar o áudio offline e aplicar a inteligência artificial depois.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: A função de download deve criar uma sub-pasta dentro de `tmp/` com o nome do `job_id`.
- **AC-002**: O sistema deve extrair metadados (duração, título, autor).
- **AC-003**: Deve salvar um `video.mp4` em até 1080p e um `audio.wav`.
- **AC-004 (Resiliência)**: Se os arquivos MP4 e WAV já existirem fisicamente na pasta, a função **pula** o download do vídeo pesado (early return), extraindo apenas o JSON de metadados.
