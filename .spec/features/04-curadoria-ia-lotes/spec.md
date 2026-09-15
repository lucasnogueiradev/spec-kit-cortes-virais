# US-004: Curadoria IA em Lotes (Chunking)

**Como** criadora de conteúdo lidando com vídeos de até 6 horas,  
**Eu quero** enviar a transcrição para a IA fatiada em lotes de 30 minutos,  
**Para que** o Google Gemini não ultrapasse seus limites gratuitos de tokens e consiga extrair os melhores cortes de cada bloco do vídeo com precisão.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: O sistema não deve tentar analisar todo o vídeo de uma vez. Deve usar uma janela de 30 minutos controlada pela variável `chunk_index`.
- **AC-002**: O Gemini Flash deve ser chamado via API REST e retornar obrigatoriamente um formato JSON estruturado com os cortes.
- **AC-003**: Cada corte retornado pela IA deve ser "enriquecido" mesclando-o com a transcrição para pegar as "words" (palavras com tempo exato relativo àquele corte).
