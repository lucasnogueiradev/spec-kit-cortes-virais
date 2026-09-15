# Tarefas de Desenvolvimento (T)

- [ ] **T-001**: Criar o arquivo `services/video_renderer.py`.
- [ ] **T-002**: Criar funções de ajuda `_seconds_to_ass_time(seconds)` e `_build_ass_content(words, duration)` para gerar o template de legendas `.ass`. A lógica do karaokê requer que o item atual `idx` tenha a tag de cor primária verde `{\c&H88FF00&}`.
- [ ] **T-003**: Atualizar a assinatura para aceitar as configurações: `def render_clip(video_path, clip, title, output_dir, render_id, layout_type="standard", template_config: dict = None, use_loop_effect=False) -> Path:`
- [ ] **T-004**: **Lógica do Efeito de Loop (Edição Não-Linear)**: Se `use_loop_effect == True` e o clip possuir `hook_start`/`hook_end`:
      - Em vez de um corte direto (linear), o `filter_complex` deve fatiar o vídeo original em duas partes usando `trim` e `atrim` (uma parte para o `hook`, outra para o vídeo principal `start:end`).
      - Deve juntar as duas partes colocando o vídeo e áudio do `hook` na frente, usando o filtro `concat=n=2:v=1:a=1`. O resultado deve ser nomeado como `[base]`.
      - Se `use_loop_effect == False`, faça o recorte linear tradicional `[0:v]...[base]`.
- [ ] **T-005**: Lógica do Layout: Em cima da `[base]`, aplique o crop/scale do `layout_type` (se for `standard` usa `crop`, se for `podcast_split` divide em 2 e usa `vstack`). O output dessa etapa chamaremos de `[layout]`.
- [ ] **T-006**: Lógica do Template (Balões e Títulos): O código Python deve olhar para `template_config`.
      - Usar `enable='between(t,0,{duration})'` baseada no tempo do template.
      - Se `type == "image"`: Usar o comando `overlay` no FFmpeg para a imagem.
      - Se `type == "code_box"`: Usar `drawbox` para criar retângulo e `drawtext` para escrever o título em cima do `[layout]`.
- [ ] **T-007**: Executar `subprocess.run(["ffmpeg", "-y", ...])`. Validar `returncode == 0`.
- [ ] **T-008**: Voltar no `main.py` e implementar as lógicas no endpoint `/render`.
