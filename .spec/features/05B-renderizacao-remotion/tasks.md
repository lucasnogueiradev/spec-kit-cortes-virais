# Tarefas de Desenvolvimento (T)

### Passo 1: Ajuste no Backend Python
- [ ] **T-001**: O arquivo `services/video_renderer.py` deve ser refatorado para NÃO chamar o `subprocess` do `ffmpeg`. 
- [ ] **T-002**: A função `render_clip` deve salvar um dicionário completo `{render_id}.json` dentro da pasta `outputs/`. Esse JSON deve conter: as `words`, `layout_type`, as configurações de `template_config` e a flag `use_loop_effect`.
- [ ] **T-003**: O backend deve retornar uma mensagem dizendo "JSON exportado com sucesso. Abra o Remotion para renderizar".

### Passo 2: O Frontend Remotion
- [ ] **T-004**: No terminal raiz, rodar o comando: `npx create-video@latest remotion-studio --template blank`.
- [ ] **T-005**: Instalar pacotes necessários (ex: `npm install react`).
- [ ] **T-006**: Criar Layouts Condicionais: Dois componentes baseados no `layout_type` recebido: `<StandardLayout />` e `<PodcastSplitLayout />`. 
- [ ] **T-007**: **Lógica do Efeito de Loop**: Se o JSON apontar que `use_loop_effect === true`:
      - Em vez de uma tag `<Video>` simples, utilize o componente `<Sequence>` do Remotion.
      - Renderize um `<Sequence>` do frame 0 até a duração do Hook, carregando o `<Video startFrom={hook_start}>`.
      - Logo em seguida, renderize o segundo `<Sequence>` começando de onde o primeiro parou, tocando o resto do vídeo (`<Video startFrom={start}>`).
      - Se `use_loop_effect === false`, toque o vídeo normalmente e de forma linear.
- [ ] **T-008**: Criar o Componente `<Banner />` para o Título que olha para `template_config` (usando `<Img>` ou CSS background, controlando a aparição pelo `currentFrame`).
- [ ] **T-009**: Criar a lógica de Legenda Karaokê com animação CSS, mapeando as `words` relativas ao `frame` atual (levando em conta o deslocamento de tempo caso o loop effect esteja ativado!).
