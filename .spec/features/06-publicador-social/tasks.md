# Tarefas de Desenvolvimento (T)

> **Nota para o Agente IA e Alunas**: Esta etapa lida com integrações corporativas. Requer paciência para criar aplicativos nos painéis do Google e Meta.

- [ ] **T-001**: Criar o arquivo `services/social_publisher.py`.
- [ ] **T-002**: Instalar as bibliotecas oficiais: `google-api-python-client`, `google-auth-oauthlib`, `requests` e `cloudinary`.
- [ ] **T-003**: Criar a assinatura principal: `def publish_video(video_path: Path, title: str, platforms: list[str]) -> dict:`
- [ ] **T-004 (YouTube Shorts)**: 
      - Ler as credenciais de `client_secrets.json`.
      - Autenticar via OAuth2 local.
      - Fazer upload do arquivo `.mp4` local diretamente definindo o metadata `snippet.title` e `status.privacyStatus` como `public`.
- [ ] **T-005 (Hospedagem Temporária - Cloudinary)**:
      - Configurar a SDK do `cloudinary` lendo as chaves do `.env`.
      - Fazer o upload do `.mp4` para o Cloudinary para obter a `secure_url` (URL pública do vídeo).
- [ ] **T-006 (Instagram Reels)**:
      - Obter o `META_ACCESS_TOKEN` e o `IG_USER_ID` do arquivo `.env`.
      - Enviar o comando para a API da Meta `POST /{ig-user-id}/media` enviando a `secure_url` obtida no Cloudinary.
      - Aguardar o status ficar "FINISHED" e fazer o `POST /{ig-user-id}/media_publish`.
- [ ] **T-007 (Limpeza)**:
      - Após publicar no Instagram, invocar a função `cloudinary.uploader.destroy()` usando o `public_id` do vídeo para apagá-lo da nuvem, economizando armazenamento do plano grátis.
- [ ] **T-008**: Retornar os status de publicação e integrar a chamada no final do endpoint assíncrono de renderização no `main.py`.
