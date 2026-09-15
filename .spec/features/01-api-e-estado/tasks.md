# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar `main.py` instanciando o FastAPI com CORS aberto. 
- [ ] **T-002**: Criar lógica de salvar e carregar dicionário de jobs do arquivo `./outputs/jobs.json`.
- [ ] **T-003**: Montar diretório estático para servir `/outputs`.
- [ ] **T-004**: Criar Pydantic Models `AnalyzeRequest` (com youtube_url, min/max duration).
- [ ] **T-005**: Criar rota `POST /analyze` que injeta tarefa em `BackgroundTasks`.
- [ ] **T-006**: Criar rota `POST /resume/{job_id}`.
- [ ] **T-007**: Criar rota `POST /analyze/{job_id}/next_batch` que incrementa o `last_analyzed_chunk_index` do estado do job e reinjeta na fila.
- [ ] **T-008**: Definir esqueleto de função assíncrona `_run_pipeline(job_id)` onde no futuro orquestraremos os próximos passos. Tratar com Try/Catch para setar `"status": "error"` se falhar.
