# US-001: API Assíncrona e Estado de Processamento

**Como** desenvolvedora/usuária do sistema,  
**Eu quero** uma API que receba a URL do meu vídeo e gerencie as tarefas em segundo plano (background),  
**Para que** meu terminal/PC não fique travado esperando horas o vídeo ser processado.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: O sistema deve conseguir inicializar lendo arquivos ou pastas (`outputs`, `tmp`).
- **AC-002**: Uma chamada POST em `/analyze` deve retornar um `job_id` quase instantaneamente e colocar a tarefa pesada de análise para rodar no fundo.
- **AC-003**: Deve existir um dicionário central persistido em um arquivo `jobs.json` (que armazene status, clips, progressos e a variável `last_analyzed_chunk_index`).
- **AC-004**: Deve existir um endpoint `POST /resume/{job_id}` e um `POST /analyze/{job_id}/next_batch` para dar suporte futuro aos lotes e pausas.
- **AC-005**: O payload da requisição de renderização (`RenderRequest`) deve permitir:
   - Um parâmetro `layout_type` (ex: `standard`, `podcast_split` ou `screenshot_reaction`).
   - Um parâmetro opcional `screenshot_image_url` (caso o usuário escolha o layout de reaction, para colocar o print no topo).
   - Um parâmetro `template_id` (ex: `impacto_vermelho`), que deve buscar a configuração visual dentro de um arquivo global `templates.json` localizado na raiz do projeto.
   - Um parâmetro booleano `use_loop_effect` (padrão: `false`). Se ativado, o renderizador aplicará uma edição não-linear, colocando o final/gancho do vídeo também no começo.
- **AC-006**: Deve existir um endpoint rápido `POST /preview` que recebe o mesmo payload do `RenderRequest`, mas em vez de processar um vídeo pesado de 1 minuto, extrai apenas 1 única foto (JPG) do vídeo com os balões, templates e print aplicados, retornando a imagem para o usuário validar o design antes de renderizar de verdade.
