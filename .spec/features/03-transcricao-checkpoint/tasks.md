# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/transcriber.py`.
- [ ] **T-002**: Criar a assinatura: `def transcribe_audio(audio_path: Path) -> list[dict]:`
- [ ] **T-003**: Fazer Checkpoint: Tentar ler o arquivo `transcript.json` no mesmo diretório do áudio. Se existir, fazer parse com `json.load` e retornar a lista imediatamente.
- [ ] **T-004**: Instanciar o `WhisperModel(model_size="small", device="cpu", compute_type="int8")` globalmente (para carregar a RAM apenas uma vez).
- [ ] **T-005**: Executar a transcrição com `word_timestamps=True`.
- [ ] **T-006**: Formatar o retorno do modelo para uma lista limpa onde cada segmento tem `start`, `end`, `text` e a lista `words`.
- [ ] **T-007**: Gravar essa lista em `transcript.json` dentro da pasta antes de dar o `return`.
- [ ] **T-008**: Integrar a chamada `transcribe_audio` no passo 2 do `_run_pipeline` no `main.py`.
