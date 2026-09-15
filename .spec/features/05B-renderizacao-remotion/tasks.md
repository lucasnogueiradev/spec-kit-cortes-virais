# Tarefas de Desenvolvimento (T)

### Passo 1: Ajuste no Backend Python
- [ ] **T-001**: O arquivo `services/video_renderer.py` deve ser refatorado para NÃO chamar o `subprocess` do `ffmpeg`. 
- [ ] **T-002**: A função `render_clip` deve pegar os dados do `clip`, o `layout_type`, e salvar como `{render_id}.json` dentro da pasta `outputs/`.
- [ ] **T-003**: O backend deve retornar uma mensagem dizendo "JSON exportado com sucesso. Abra o Remotion para renderizar".

### Passo 2: O Frontend Remotion
- [ ] **T-004**: No terminal raiz, rodar o comando: `npx create-video@latest remotion-studio --template blank`.
- [ ] **T-005**: Instalar pacotes necessários (ex: `npm install react` caso falte algo).
- [ ] **T-006**: Criar dois componentes React baseados no `layout_type` recebido no JSON: `<StandardLayout />` e `<PodcastSplitLayout />`.
- [ ] **T-007**: No `<PodcastSplitLayout />`, posicione `<Video>` duas vezes na tela usando flexbox, aplicando cortes (ex: `object-position: left center` e `right center`) para criar a tela dividida.
- [ ] **T-008**: Desenhar o Título no topo da tela com CSS puro (cores vivas, sombra).
- [ ] **T-009**: Criar a lógica de Legenda Karaokê com animação, mapeando as `words` relativas ao `frame` atual.
