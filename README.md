# hyse

Canal oficial de distribuição do hyse para Windows x64.

Baixe a release estável mais recente em **Releases**. A 0.13.0 introduz o atualizador: instale-a uma vez por cima da instalação existente. Depois disso, futuras versões assinadas são baixadas em segundo plano e aplicadas ao escolher Sair ou Reiniciar e atualizar em Configurações → App info. O X continua ocultando a janela na bandeja.

Conta, playlists, histórico, perfil e configurações são preservados. O código correspondente completo acompanha o ZIP e o Setup; `source/current.zip` registra a fonte usada pelo fluxo de compilação. Licenças e avisos ficam nos pacotes.

## Publicação

O workflow **Build hyse release** compila e testa a fonte, envia instalador/ZIP/hashes a um rascunho e registra o manifesto sem assinatura em `pending/hyse-update.json`. Uma assinatura RSA correspondente à chave pública do aplicativo deve ser gerada fora do GitHub. A chave privada nunca é publicada nem armazenada nos workflows.

Ao enviar o manifesto exato e sua assinatura base64 a `signed/`, **Publish signed hyse release** confere a assinatura e o instalador, envia o feed à release e só então publica o canal estável. Atualizações de fonte acionam uma nova compilação; cada versão deve ter número maior e passar os testes. Não se reutiliza uma versão já publicada.

Os testes automatizados e o cross-build não substituem validar o instalador no Windows.
