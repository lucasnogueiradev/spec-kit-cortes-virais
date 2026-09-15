# US-006: Publicador Social Automático (100% Gratuito)

**Como** criadora de conteúdo que produz dezenas de cortes por dia,  
**Eu quero** que o sistema envie automaticamente o vídeo pronto para minhas redes sociais (TikTok, Reels, Shorts) usando os canais oficiais,  
**Para que** eu não tenha custos com ferramentas de terceiros e meu aplicativo rode de forma legítima, sem risco de ser banido por comportamento de robô.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: O sistema não deve tentar fazer "Web Scraping", pois plataformas como Instagram bloqueiam o envio de Reels pelo navegador tradicional.
- **AC-002**: O sistema deve utilizar as APIs oficiais de cada plataforma (ex: `YouTube Data API v3` e `Meta Graph API`).
- **AC-003**: Deve existir um arquivo `.env` para armazenar os tokens de acesso gerados nos painéis de desenvolvedor (Meta for Developers e Google Cloud Console).
- **AC-004**: O sistema deve enviar o vídeo final `.mp4` juntamente com o `title` gerado pela IA no passo 04, embutindo hashtags.
- **AC-005**: Como a API do Instagram exige que o vídeo esteja online em uma URL pública (e não num arquivo local), o sistema deve fazer o upload temporário do vídeo para a nuvem gratuita do **Cloudinary**.
- **AC-006**: Após o vídeo ser postado com sucesso no Instagram, o sistema deve executar um job de limpeza que exclui o arquivo do Cloudinary para não estourar o limite da conta gratuita.
