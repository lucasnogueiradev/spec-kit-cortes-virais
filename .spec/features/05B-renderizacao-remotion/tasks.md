# Tarefas de Desenvolvimento (T)

### Passo 1: Ajuste no Backend Python
- [ ] **T-001**: O arquivo `services/video_renderer.py` deve ser refatorado para NÃO chamar o `subprocess` do `ffmpeg`. 
- [ ] **T-002**: A função `render_clip` deve pegar os dados do `clip` (especialmente as `words`), criar um dicionário estruturado e salvá-lo como `{render_id}.json` dentro da pasta `outputs/`.
- [ ] **T-003**: O backend deve retornar uma mensagem dizendo "JSON exportado com sucesso. Abra o Remotion para renderizar".

### Passo 2: O Frontend Remotion
- [ ] **T-004**: No terminal raiz, rodar o comando: `npx create-video@latest remotion-studio --template blank` (ou similar) para instanciar o ambiente.
- [ ] **T-005**: Instalar pacotes necessários (ex: `npm install react` caso falte algo).
- [ ] **T-006**: Criar um componente `<ViralReel />` que usa `useVideoConfig` e `useCurrentFrame` do Remotion.
- [ ] **T-007**: Carregar dinamicamente o JSON exportado pelo Python e o MP4 original (`<Video src={...} />`).
- [ ] **T-008**: Desenhar o Título no topo da tela com CSS puro (cores vivas, sombra).
- [ ] **T-009**: Criar a lógica de Legenda Karaokê: Use `frame` e `fps` para calcular os segundos atuais. Filtre as `words` do JSON para encontrar a palavra que está sendo dita no momento, e aplique uma classe CSS (ex: `font-size: 1.5em; text-shadow: neon;`) apenas nela.
