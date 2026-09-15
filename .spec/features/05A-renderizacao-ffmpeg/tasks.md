# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/video_renderer.py`.
- [ ] **T-002**: Criar funções de ajuda `_seconds_to_ass_time(seconds)` e `_build_ass_content(words, duration)` para gerar o template de legendas `.ass`. A lógica do karaokê requer que o item atual `idx` tenha a tag de cor primária verde `{\c&H88FF00&}`.
- [ ] **T-003**: Atualizar a assinatura para aceitar as configurações de design: `def render_clip(video_path, clip, title, output_dir, render_id, layout_type="standard", template_config: dict = None) -> Path:`
- [ ] **T-004**: Lógica do Layout: Montar a base do `filter_complex` baseada no `layout_type` (se for `standard` usa `crop`, se for `podcast_split` usa `vstack`). O output dessa etapa chamaremos de `[base]`.
- [ ] **T-005**: Lógica do Template (Balões e Títulos): O código Python deve olhar para `template_config` (que veio do `templates.json` global).
      - Tempo de tela: Construir a string `enable='between(t,0,{duration})'` baseada em `template_config["duration_seconds"]`.
      - Se `type == "image"`: Usar o comando `overlay` no FFmpeg para posicionar o arquivo `asset_path` no Y desejado.
      - Se `type == "code_box"`: Usar o comando `drawbox` para criar o retângulo.
      - Por fim, usar `drawtext` para escrever o título (aplicando a mesma regra de `enable` de duração).
- [ ] **T-006**: Executar `subprocess.run(["ffmpeg", "-y", "-ss", start, "-t", duration, "-i", video_path, "-filter_complex", filter_complex, ...])`. Validar `returncode == 0`.
- [ ] **T-007**: Voltar no `main.py` e implementar as lógicas de `_run_render(render_id, job, req)`, lendo o arquivo local `templates.json` e repassando o bloco de configuração inteiro para a função de renderização.
