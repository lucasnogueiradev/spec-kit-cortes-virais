# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/downloader.py`.
- [ ] **T-002**: Implementar `def download_video(youtube_url: str, temp_dir: Path, job_id: str)`.
- [ ] **T-003**: Fazer a checagem de Checkpoint: `if (job_dir / "video.mp4").exists() and (job_dir / "audio.wav").exists():` retorne metadados pulando o shell.
- [ ] **T-004**: Criar lógica de Segurança/Anti-Bot: Antes de executar o `yt-dlp`, verifique se existe um arquivo `cookies.txt` na raiz do projeto. Se existir, adicione a flag `--cookies cookies.txt` na lista de argumentos base do yt-dlp.
- [ ] **T-005**: Executar `yt-dlp --dump-json --extractor-args "youtube:player_client=android" [FLAGS_DE_COOKIE_SE_EXISTIR]` via `subprocess.run` para obter título e informações básicas do canal.
- [ ] **T-006**: Executar `yt-dlp` com os mesmos argumentos para baixar o `video.mp4` (formato best/1080p máximo) e um arquivo extra `audio.wav` separado.
- [ ] **T-007**: Retornar a tupla `(video_path, audio_path, metadata)`.
- [ ] **T-008**: Integrar a chamada de `download_video` dentro do passo 1 da função `_run_pipeline` do `main.py`.
