# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/video_renderer.py`.
- [ ] **T-002**: Criar funções de ajuda `_seconds_to_ass_time(seconds)` para legendar.
- [ ] **T-003**: Atualizar a assinatura: `def render_clip(..., bg_music=None, bg_volume=0.1) -> Path:`
- [ ] **T-004 (Lógica do Efeito de Loop)**: 
      - Fazer `trim` e `concat` das partes visuais e de áudio se `use_loop_effect == True`.
- [ ] **T-005 (Trilha Sonora de Fundo)**: Se `bg_music` for passado:
      - O FFmpeg deverá receber um input extra `-i assets/music/{bg_music}`.
      - Na cadeia de filtros complexos (`-filter_complex`), pegar o áudio da música e baixar o volume usando `volume={bg_volume}`. Em seguida, misturar com o áudio falado usando `amix=inputs=2:duration=first`. Isso garante que a música de fundo nunca cubra a voz da pessoa, e que ela pare de tocar exatamente quando o vídeo acabar.
- [ ] **T-006 (Lógica do Layout Visual)**: 
      - Aplicar `standard`, `podcast_split` ou `screenshot_reaction` via `vstack` e escala.
- [ ] **T-007 (Balões e Títulos)**:
      - Aplicar `drawbox` e `overlay` baseado no `templates.json`.
- [ ] **T-008**: Executar `subprocess.run(["ffmpeg", "-y", ...])`. Validar `returncode == 0`.
- [ ] **T-009**: Criar função `generate_preview_frame(...)` com `-vframes 1` para fotos estáticas.
