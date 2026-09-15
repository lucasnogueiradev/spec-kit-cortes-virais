# US-05B: Renderização Visual Dinâmica com Remotion (React)

**Como** publicadora em redes sociais apaixonada por design,  
**Eu quero** que o backend exporte apenas um arquivo de metadados estruturado (JSON), e que o vídeo seja renderizado por um projeto React (Remotion),  
**Para que** eu possa criar legendas com efeitos neon, usar Google Fonts e visualizar as alterações no navegador (HTML/CSS) antes de exportar o MP4 final, no estilo exato do TikTok.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001 (Backend)**: O Worker em Python NÃO deve rodar o FFmpeg. O endpoint `/render` deve apenas pegar as `words` exatas, os timestamps, o `title` do corte selecionado, e salvar um arquivo limpo chamado `remotion_input.json` na pasta `/outputs`.
- **AC-002 (Frontend)**: Deve existir uma pasta separada chamada `/remotion-studio` iniciada com `npx create-video`.
- **AC-003**: O projeto Remotion deve ler o `remotion_input.json`, carregar o arquivo MP4 do vídeo bruto, e exibir o título e as legendas perfeitamente sincronizadas através de componentes React.
- **AC-004**: A fonte e a animação ("pop-in") da legenda devem ser estilizadas via CSS/React.
