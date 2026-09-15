# Tarefas de Desenvolvimento (T)

> **Nota para o Agente IA**: Este módulo trata do Frontend. O Backend Python já está pronto nas Specs de 01 a 06. 

- [ ] **T-001**: Inicializar o projeto frontend executando: `npx create-next-app@latest frontend --typescript --tailwind --eslint --app`.
- [ ] **T-002 (Design System & Tailwind)**:
      - Configurar a importação da fonte `Nunito` (do `next/font/google`) no `layout.tsx` para garantir uma tipografia moderna e arredondada.
      - No `tailwind.config.ts`, configurar a paleta de cores adicionando o vermelho específico do projeto:
        ```typescript
        theme: {
          extend: {
            colors: {
              brand: '#f2183c',
              background: '#0a0a0a',
              surface: '#171717'
            }
          }
        }
        ```
      - No `globals.css`, forçar o fundo do body para a cor `background` e o texto para branco, implementando o Dark Mode definitivo.
      - Criar componentes básicos de UI (ex: `<Button className="bg-brand text-white rounded-full hover:opacity-90" />`).
- [ ] **T-003 (Autenticação)**: 
      - Instalar a biblioteca `next-auth`. 
      - Configurar o provedor `TwitchProvider` passando as credenciais do `.env.local`.
      - Criar a rota de API em `app/api/auth/[...nextauth]/route.ts`.
- [ ] **T-004 (Componente de Galeria)**:
      - Criar uma página que utilize o token OAuth recebido para fazer um `GET` na Twitch API (`https://api.twitch.tv/helix/videos?user_id=me`).
      - Renderizar uma grade de vídeos, exibindo `thumbnail_url` e `title`.
- [ ] **T-005 (Integração com Backend Python)**:
      - Ao clicar num card da galeria, fazer um `fetch("http://localhost:8000/analyze", { method: "POST", body: JSON.stringify({ video_url: twitch_url }) })`.
      - Salvar o `job_id` retornado.
- [ ] **T-006 (Tela de Processamento)**:
      - Criar um componente que faça polling chamando `/resume/{job_id}`. Quando o status retornar `CURATION_DONE`, exibir os clipes na tela.
- [ ] **T-007 (Renderização e Preview)**:
      - Para cada clipe, exibir um formulário com opções de `layout_type` e um botão de `Preview`. O preview faz POST no Python e renderiza a foto gerada pelo FFmpeg.
      - Botão final de `Publicar` (`POST /render` com `auto_publish=true`).
