# US-001: API Assíncrona e Estado de Processamento

**Como** desenvolvedora/usuária do sistema,  
**Eu quero** uma API que receba a URL do meu vídeo e gerencie as tarefas em segundo plano (background),  
**Para que** meu terminal/PC não fique travado esperando horas o vídeo ser processado.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: O sistema deve conseguir inicializar lendo arquivos ou pastas (`outputs`, `tmp`).
- **AC-002**: Uma chamada POST em `/analyze` deve retornar um `job_id` quase instantaneamente e colocar a tarefa pesada de análise para rodar no fundo.
- **AC-003**: Deve existir um dicionário central persistido em um arquivo `jobs.json` (que armazene status, clips, progressos e a variável `last_analyzed_chunk_index`).
- **AC-004**: Deve existir um endpoint `POST /resume/{job_id}` e um `POST /analyze/{job_id}/next_batch` para dar suporte futuro aos lotes e pausas.
- **AC-005**: O payload da requisição de renderização (`RenderRequest`) deve permitir um parâmetro opcional chamado `layout_type` (ex: `standard` ou `podcast_split`), para dar flexibilidade ao editor final.
