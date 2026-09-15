# Tarefas de Desenvolvimento (T)

### Passo 1: Ajuste no Backend Python
- [ ] **T-001**: O arquivo `services/video_renderer.py` deve ser refatorado para NÃO chamar o `subprocess` do `ffmpeg`. 
- [ ] **T-002**: A função `render_clip` deve ler o arquivo `templates.json` e injetar a configuração visual completa, junto com o `layout_type`, nas opções do arquivo de saída `{render_id}.json` dentro da pasta `outputs/`.
- [ ] **T-003**: O backend deve retornar uma mensagem dizendo "JSON exportado com sucesso. Abra o Remotion para renderizar".

### Passo 2: O Frontend Remotion
- [ ] **T-004**: No terminal raiz, rodar o comando: `npx create-video@latest remotion-studio --template blank`.
- [ ] **T-005**: Instalar pacotes necessários (ex: `npm install react`).
- [ ] **T-006**: Criar Layouts Condicionais: Dois componentes baseados no `layout_type` recebido: `<StandardLayout />` e `<PodcastSplitLayout />`. No Podcast, use flexbox para fatiar o vídeo original.
- [ ] **T-007**: Criar o Componente `<Banner />` para o Título. Ele deve olhar para a propriedade `template_config` que veio no JSON.
      - Use `if (currentFrame > duration * fps) return null;` para controlar o tempo de tela do balão.
      - Se `type === "image"`, exiba uma `<Img src={asset_path} />`.
      - Se `type === "code_box"`, exiba uma `div` com `backgroundColor`.
      - Ajuste a posição Y através de `style={{ top: config.position_y }}`.
- [ ] **T-008**: Criar a lógica de Legenda Karaokê com animação CSS, mapeando as `words` relativas ao `frame` atual.
