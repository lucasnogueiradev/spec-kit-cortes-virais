# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/video_renderer.py`.
- [ ] **T-002**: Criar funções de ajuda `_seconds_to_ass_time(seconds)` e `_build_ass_content(words, duration)` para gerar legendas `.ass` coloridas (ex: verde).
- [ ] **T-003**: Atualizar a assinatura: `def render_clip(video_path, clip, title, output_dir, render_id, layout_type="standard", template_config: dict = None, use_loop_effect=False, screenshot_path=None) -> Path:`
- [ ] **T-004**: **Lógica do Efeito de Loop (Edição Não-Linear)**: Se `use_loop_effect == True` e o clip possuir `hook_start`/`hook_end`:
      - Fatiar o vídeo original em duas partes usando `trim` e `atrim` e juntá-las usando `concat=n=2:v=1:a=1`. O resultado será chamado `[base]`.
      - Se `use_loop_effect == False`, faça o recorte linear tradicional `[0:v]...[base]`.
- [ ] **T-005**: Lógica do Layout: Em cima da `[base]`, aplique a organização visual:
      - Se `standard`: `[base]scale=...,crop...[layout]`.
      - Se `podcast_split`: Fatie a `[base]` em cima e embaixo, e faça `vstack`.
      - Se `screenshot_reaction`: Adicione o arquivo da imagem como segundo input (`-i screenshot_path`). Escale a imagem para a metade de cima (1080x960), escale o vídeo `[base]` para a metade de baixo, e use `vstack` para colar os dois. O output será o `[layout]`.
- [ ] **T-006**: Lógica do Template (Balões e Títulos): O código Python deve olhar para `template_config` (que conterá as posições e o tempo de exibição `duration_seconds`).
      - Para fazer a "tarja vermelha no meio", o JSON de template já deve ter a posição Y próxima do meio da tela (ex: Y=900).
      - Aplicar `drawbox` ou `overlay` em cima do `[layout]`.
- [ ] **T-007**: Executar `subprocess.run(["ffmpeg", "-y", ...])`. Validar `returncode == 0`.
- [ ] **T-008 (Geração de Preview)**: Criar uma função secundária `generate_preview_frame(...)`. Ela reaproveita toda a lógica do `filter_complex` acima, mas na hora de rodar o `ffmpeg`, ela deve pular pro meio do vídeo (ex: `-ss 10`), usar o argumento `-vframes 1` e exportar como um arquivo `.jpg`. Isso gera a imagem de teste instantaneamente sem processar os outros 1.799 frames.
- [ ] **T-009**: Integrar as chamadas no endpoint `/render` e `/preview` no arquivo `main.py`.
