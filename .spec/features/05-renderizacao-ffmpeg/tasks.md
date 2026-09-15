# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/video_renderer.py`.
- [ ] **T-002**: Criar funções de ajuda `_seconds_to_ass_time(seconds)` e `_build_ass_content(words, duration)` para gerar o template de legendas `.ass`. A lógica do karaokê requer que o item atual `idx` tenha a tag de cor primária verde `{\c&H88FF00&}`.
- [ ] **T-003**: Criar a assinatura: `def render_clip(video_path, clip, title, output_dir, render_id) -> Path:`
- [ ] **T-004**: Montar a string do `filter_complex` do ffmpeg. Exemplo: `[0:v]scale=1080:1920:force_original_aspect_ratio=increase,crop=1080:1920[composite];[composite]drawbox=x=0:y=180:w=1080:h=230:color=#E50914@1:t=fill,drawtext=text='{title_line_1}':fontcolor=white:fontsize=75:x=(w-text_w)/2:y=210[titled];[titled]ass='{ass_path}'[out]`
- [ ] **T-005**: Executar `subprocess.run(["ffmpeg", "-y", "-ss", start, "-t", duration, "-i", video_path, "-filter_complex", filter_complex, ...])`. Validar `returncode == 0`.
- [ ] **T-006**: Voltar no `main.py` e implementar as lógicas de `_run_render(render_id, job, req)` assíncrono chamado pelas rotas `/render` e `/render/status`.
