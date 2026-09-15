# Tarefas de Desenvolvimento (T)

### Passo 1: Ajuste no Backend Python
- [ ] **T-001**: O arquivo `services/video_renderer.py` deve ser refatorado para NÃO chamar o `subprocess` do `ffmpeg`. 
- [ ] **T-002**: A função `render_clip` deve salvar um dicionário `{render_id}.json` dentro da pasta `outputs/`. Esse JSON deve conter: as `words`, `layout_type`, `screenshot_image_url`, as configurações de `template_config` e a flag `use_loop_effect`.
- [ ] **T-003**: O backend deve retornar uma mensagem dizendo "JSON exportado com sucesso. Abra o Remotion para renderizar ou gerar o Preview".

### Passo 2: O Frontend Remotion
- [ ] **T-004**: No terminal raiz, rodar o comando: `npx create-video@latest remotion-studio --template blank`.
- [ ] **T-005**: Instalar pacotes necessários (ex: `npm install react`).
- [ ] **T-006**: Criar Layouts Condicionais: Três componentes baseados no `layout_type`:
      - `<StandardLayout />`: Tela inteira.
      - `<PodcastSplitLayout />`: Flexbox com 2 recortes de vídeo.
      - `<ScreenshotReactionLayout />`: Flexbox vertical. A metade superior será uma `<Img src={screenshot_image_url} />`, e a metade inferior será o componente de `<Sequence>` de vídeo.
- [ ] **T-007**: **Lógica do Efeito de Loop**: Se o JSON apontar que `use_loop_effect === true`:
      - Renderize um `<Sequence>` inicial com a duração do Hook, tocando a parte final do vídeo.
      - Logo em seguida, renderize o segundo `<Sequence>`, tocando o resto do vídeo.
- [ ] **T-008**: Criar o Componente `<Banner />` para a "Tarja vermelha no meio". Ele deve olhar para a propriedade `template_config` para ajustar a cor e posicioná-lo no meio da tela (`top: 50%`), controlando a aparição pelo `currentFrame`.
- [ ] **T-009**: Criar a lógica de Legenda Karaokê com animação CSS, renderizando o texto em sincronia com as `words`.
- [ ] **T-010 (Geração de Preview)**: Utilizar o comando CLI do Remotion `npx remotion still ...` passando as props do JSON para extrair um `.jpeg` estático de um frame central (ex: `--frame=300`). Isso atende ao endpoint `/preview` gerando uma foto sem gastar recursos pesados.
