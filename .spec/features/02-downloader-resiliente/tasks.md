# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/downloader.py`.
- [ ] **T-002**: Implementar `def download_video(youtube_url: str, temp_dir: Path, job_id: str)`.
- [ ] **T-003**: Fazer a checagem de Checkpoint: `if (job_dir / "video.mp4").exists() and (job_dir / "audio.wav").exists():` retorne metadados pulando o shell.
- [ ] **T-004**: Executar `yt-dlp --dump-json --extractor-args "youtube:player_client=android"` via `subprocess.run` para obter título e informações básicas do canal.
- [ ] **T-005**: Executar `yt-dlp` para baixar o `video.mp4` (formato best/1080p máximo) e um arquivo extra `audio.wav` separado.
- [ ] **T-006**: Retornar a tupla `(video_path, audio_path, metadata)`.
- [ ] **T-007**: Integrar a chamada de `download_video` dentro do passo 1 da função `_run_pipeline` do `main.py`.
