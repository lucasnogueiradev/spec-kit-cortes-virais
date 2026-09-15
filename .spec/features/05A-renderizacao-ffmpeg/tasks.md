# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/video_renderer.py`.
- [ ] **T-002**: Criar funções de ajuda `_seconds_to_ass_time(seconds)` e `_build_ass_content(words, duration)` para gerar o template de legendas `.ass`. A lógica do karaokê requer que o item atual `idx` tenha a tag de cor primária verde `{\c&H88FF00&}`.
- [ ] **T-003**: Atualizar a assinatura: `def render_clip(video_path, clip, title, output_dir, render_id, layout_type="standard") -> Path:`
- [ ] **T-004**: Montar a string do `filter_complex` baseada no `layout_type`. 
      - Se `layout_type == "standard"`: Faça crop 1080x1920 centralizado no vídeo inteiro. Ex: `[0:v]scale=1080:1920:force_original_aspect_ratio=increase,crop=1080:1920[composite];...`
      - Se `layout_type == "podcast_split"`: Faça dois recortes (um para o topo pegando a esquerda, outro para a base pegando a direita) e junte-os usando `vstack`. Ex: `[0:v]crop=iw/2:ih:0:0,scale=1080:960[top]; [0:v]crop=iw/2:ih:iw/2:0,scale=1080:960[bottom]; [top][bottom]vstack[composite];...`
- [ ] **T-005**: Adicionar a caixa e texto (Título) em cima do frame `[composite]`.
- [ ] **T-006**: Executar `subprocess.run(["ffmpeg", "-y", "-ss", start, "-t", duration, "-i", video_path, "-filter_complex", filter_complex, ...])`. Validar `returncode == 0`.
- [ ] **T-007**: Voltar no `main.py` e implementar as lógicas de `_run_render(render_id, job, req)` assíncrono chamado pelas rotas `/render` e `/render/status`, repassando o `layout_type`.
