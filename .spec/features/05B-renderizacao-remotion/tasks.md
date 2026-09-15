# Tarefas de Desenvolvimento (T)

### Passo 1: Ajuste no Backend Python
- [ ] **T-001**: O arquivo `services/video_renderer.py` deve ser refatorado para NÃO chamar o `subprocess` do `ffmpeg`. 
- [ ] **T-002**: A função `render_clip` deve salvar um dicionário `{render_id}.json` dentro da pasta `outputs/`. Esse JSON deve conter: as configurações de layout, `use_loop_effect`, e agora também `bg_music_url` e `bg_volume`.
- [ ] **T-003**: Retornar sucesso.

### Passo 2: O Frontend Remotion
- [ ] **T-004**: No terminal raiz, rodar o comando: `npx create-video@latest remotion-studio --template blank`.
- [ ] **T-005**: Instalar pacotes necessários (ex: `npm install react`).
- [ ] **T-006 (Trilha Sonora de Fundo)**:
      - Se a propriedade `bg_music_url` estiver presente no JSON, renderizar o componente nativo do Remotion `<Audio src={bg_music_url} volume={bg_volume} loop />`. O Remotion cuidará de fazer a música tocar suavemente no fundo em repetição.
- [ ] **T-007**: Criar Layouts Condicionais (`<StandardLayout />`, `<PodcastSplitLayout />`, `<ScreenshotReactionLayout />`).
- [ ] **T-008 (Efeito Loop)**: Usar dois componentes `<Sequence>` alternando os tempos iniciais do vídeo.
- [ ] **T-009**: Criar o Componente `<Banner />` para a Tarja baseada no template.
- [ ] **T-010**: Criar a lógica de Legenda Karaokê com animação CSS.
- [ ] **T-011**: Utilizar `npx remotion still` para o sistema de Preview Rápido.
