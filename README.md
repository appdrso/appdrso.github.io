# Host público DRSO

Espelho dos dois pontos de entrada de `appdrso5crpm/appdrso5crpm.github.io`. Ambos devem ter o mesmo conteúdo.

Os favicons ativos são `assets/favicon-16-v0863.png`, `assets/favicon-32-v0863.png` e `assets/favicon-64-v0863.png`: derivados da marca aprovada com o policial voltado à direita, com enquadramento circular de 220 × 220 px para eliminar a margem que diminuía o desenho na aba. `favicon.ico` contém as três imagens, nos respectivos tamanhos nativos. Os ícones de instalação permanecem na família `v0860`. Os arquivos anteriores são mantidos para clientes com páginas em cache.

Para regenerar os favicons, execute `node scripts/build-favicons.cjs` com ImageMagick 6 instalado. O PNG original de 256 px em `assets/DRSO-MARCA.png` permanece intacto.

O protocolo de incorporação valida origem, fonte e nonce. A URL `/exec` aponta à implantação existente; publicar este host não implanta o Google Apps Script.

## Abertura em navegador normal — 0.8.6.4

[Acesso atualizado](https://appdrso5crpm.github.io/acesso.html?v=0.8.6.4). O parâmetro de versão cria uma entrada distinta no cache HTTP, sem exigir limpeza dos dados do navegador.

O iframe usa o endereço canônico `/macros/s/.../exec?authuser=0&embed=1`. Nos navegadores compatíveis, recebe `credentialless` **antes da primeira navegação**, separando a abertura dos cookies das contas Google já conectadas. A r1 aguardava 20 segundos antes de fazer isso. O acesso `/?recuperar=1` continua compatível, agora com o mesmo comportamento da entrada comum.

O isolamento é temporário: recarregar pode exigir novo login no DRSO. Ele não desconecta contas Google, não altera as senhas e não dispensa a autenticação própria do DRSO. Navegadores sem esse recurso conservam a abertura canônica e o botão de nova tentativa; não há promessa de isolamento neles.

Somente a confirmação do DRSO, com origem, janela e nonce válidos, encerra o acompanhamento da abertura. Uma indisponibilidade mostra os controles após 20 segundos; não inicia ciclos automáticos. O botão **Tentar novamente** cria outro iframe e recusa mensagens do quadro removido.

`scripts/persistent-access-audit.cjs` exercita um perfil Chromium persistente, reaberto com cookie sintético e cache HTTP real. O teste não intercepta requisições. Uma simulação HTTPS mede os cookies recebidos no servidor e a abertura por endereço versionado. A conferência pública acessa apenas os logins USER/ADMIN, sem enviar formulários.

Demonstrações antigas não fazem parte do host. A prévia atual é gerada em `delivery/` com dados fictícios.

A versão 0.8.6.4 mostra a marca DRSO e um anel de carregamento até a confirmação do aplicativo. A margem transparente da imagem original é enquadrada por CSS, sem redesenhar a arte. A animação respeita a preferência por movimento reduzido. O host acompanha a altura do viewport visual para disponibilizar ao formulário o espaço restante quando o teclado abre.

## Matrícula e teclado — 0.8.6.6

O host acompanha altura e deslocamento (`offsetTop`) do viewport visual, ouvindo resize e scroll. A mudança é aplicada somente com escala 1. A matrícula do último acesso bem-sucedido é mantida em `localStorage` sob `drso.registration`, com 5–8 dígitos e zeros iniciais; nenhum PIN ou dado de perfil acompanha esse recurso. O host só aceita a mensagem de gravação da origem, janela e nonce aprovados após READY. Uma nova aprovação aguarda outro READY; mensagens do iframe removido são recusadas. O login pode funcionar quando o navegador bloqueia armazenamento.

[Acesso atualizado 0.8.6.6](https://appdrso5crpm.github.io/acesso.html?v=0.8.6.6). Credenciais previamente salvas pelo navegador conservam seus próprios rótulos. Os testes do host incorporam a interface real com dados fictícios e simulam altura de 360 px e deslocamento de 120 px; não reproduzem um teclado físico de iOS.
