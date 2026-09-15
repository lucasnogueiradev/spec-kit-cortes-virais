# US-003: Transcrição em Texto com Checkpoint

**Como** estudante processando áudio localmente,  
**Eu quero** usar a inteligência do Whisper para transformar fala em texto identificando o milissegundo exato de cada palavra,  
**Para que** eu consiga gerar as legendas animadas em formato de Karaokê mais tarde.

### Como sei que funcionou (Critérios de Aceite)

- **AC-001**: O sistema deve rodar o modelo `faster-whisper` em CPU (para não dar erro no meu computador local que não tem placa Nvidia).
- **AC-002**: O JSON final retornado pela função precisa dizer onde a palavra começou (`start`) e onde terminou (`end`).
- **AC-003 (Resiliência)**: Se a luz cair ou o programa reiniciar depois que a transcrição (que demora horas) já tiver terminado, o programa deve usar o arquivo `transcript.json` salvo na pasta em vez de rodar a IA tudo de novo.
