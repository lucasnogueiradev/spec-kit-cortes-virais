# US-007: Painel SaaS e Integração com Plataformas (Frontend)

**Como** criadora de conteúdo e usuária final do sistema,  
**Eu quero** acessar um painel visual no meu navegador, conectar minha conta da Twitch/YouTube e escolher um vídeo da minha galeria,  
**Para que** eu não precise usar o terminal de comandos e o sistema seja fácil de usar como um "Software as a Service".

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: O frontend deve ser construído em um ecossistema React moderno (ex: Next.js).
- **AC-002**: Deve possuir um **Design System Padronizado** obrigatório:
  - **Tema Base**: Dark Mode (tons escuros de cinza/preto para fundo).
  - **Cor Primária (Brand)**: Vermelho vibrante (`#f2183c` ou `rgb(242, 24, 60)`) para botões de ação e detalhes visuais.
  - **Tipografia**: Fonte moderna e arredondada (recomenda-se `Nunito` ou `Poppins` via Google Fonts).
- **AC-003**: Deve haver um botão de autenticação OAuth2 (ex: "Login com Twitch").
- **AC-004**: Após logar, o sistema deve exibir os últimos VODs (Vídeos) da conta do usuário em formato de grade (Galeria), mostrando a capa e o título.
- **AC-005**: Ao clicar em um vídeo, o painel deve fazer um POST para o endpoint `/analyze` do nosso Backend Python (Spec 01), sem que a usuária precise copiar a URL manualmente.
- **AC-006**: O painel deve exibir uma tela de carregamento lendo o status do Backend (`/resume/{job_id}`) até que a IA termine a curadoria.
- **AC-007**: O painel deve exibir os cortes gerados pela IA e oferecer opções visuais (Botões) para escolher o `layout_type`, exibir um "Preview Instantâneo" e publicar.
