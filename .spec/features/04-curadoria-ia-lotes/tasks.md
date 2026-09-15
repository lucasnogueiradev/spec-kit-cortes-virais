# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/ai_curator.py`.
- [ ] **T-002**: Criar a assinatura: `def curate_clips(transcript: list[dict], video_info: dict, min_duration: int, max_duration: int, num_clips: int = 6, chunk_index: int = 0) -> list[dict]:`
- [ ] **T-003**: Implementar fatiamento (Chunking): Filtre a lista `transcript` para conter apenas segmentos onde o tempo de início (`start`) caia entre `(chunk_index * 1800)` e `((chunk_index + 1) * 1800)`. Se a fatia estiver vazia, lance uma Exception "Fim do vídeo atingido".
- [ ] **T-004**: Montar o Prompt pedindo para o LLM extrair no máximo `{num_clips}` cortes desta fatia de transcrição e retornar ESTRITAMENTE em formato JSON (contendo start, end, title, score). 
      - **IMPORTANTE:** Peça também para a IA identificar a frase de "gancho" (hook) mais chocante/curiosa dentro do corte (pode ser no final ou no meio) e preencher um bloco `hook_start` e `hook_end`. Isso será útil caso o usuário queira aplicar o efeito de Loop.
- [ ] **T-005**: Fazer a chamada HTTP via `requests.post` para `gemini-2.5-flash:generateContent`.
- [ ] **T-006**: Ler o JSON retornado. Para cada corte, faça um loop de volta na fatia do transcript e extraia as `words` exatas daquele tempo. Recalcule o timestamp das `words` para ser relativo ao `start` do corte principal.
- [ ] **T-007**: Retornar os clipes ordenados por score.
- [ ] **T-008**: Integrar a chamada `curate_clips` no passo 3 do `_run_pipeline` no `main.py`, lendo a variável `last_analyzed_chunk_index` do dict do job.
