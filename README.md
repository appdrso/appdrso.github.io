# Host público DRSO

Espelho dos dois pontos de entrada de `appdrso/appdrso.github.io`. Ambos devem ter o mesmo conteúdo.

Os favicons ativos são `assets/favicon-16-v0862.png`, `assets/favicon-32-v0862.png` e `assets/favicon-64-v0862.png`: cópias dos arquivos aprovados com o policial voltado à direita. `favicon.ico` contém as três imagens, sem reamostragem. Os ícones de instalação permanecem na família `v0860`. Os arquivos anteriores são mantidos para clientes com páginas em cache.

O protocolo de incorporação valida origem, fonte e nonce. A URL `/exec` aponta à implantação existente; publicar este host não implanta o Google Apps Script.

## Abertura em navegador normal — 0.8.6.2

[Acesso atualizado](https://appdrso.github.io/acesso.html?v=0.8.6.2). O parâmetro de versão cria uma entrada distinta no cache HTTP, sem exigir limpeza dos dados do navegador.

O iframe usa o endereço canônico `/macros/s/.../exec?authuser=0&embed=1`. Nos navegadores compatíveis, recebe `credentialless` **antes da primeira navegação**, separando a abertura dos cookies das contas Google já conectadas. A r1 aguardava 20 segundos antes de fazer isso. O acesso `/?recuperar=1` continua compatível, agora com o mesmo comportamento da entrada comum.

O isolamento é temporário: recarregar pode exigir novo login no DRSO. Ele não desconecta contas Google, não altera as senhas e não dispensa a autenticação própria do DRSO. Navegadores sem esse recurso conservam a abertura canônica e o botão de nova tentativa; não há promessa de isolamento neles.

Somente a confirmação do DRSO, com origem, janela e nonce válidos, encerra o acompanhamento da abertura. Uma indisponibilidade mostra os controles após 20 segundos; não inicia ciclos automáticos. O botão **Tentar novamente** cria outro iframe e recusa mensagens do quadro removido.

`scripts/persistent-access-audit.cjs` exercita um perfil Chromium persistente, reaberto com cookie sintético e cache HTTP real. O teste não intercepta requisições. Uma simulação HTTPS mede os cookies recebidos no servidor e a abertura por endereço versionado. A conferência pública acessa apenas os logins USER/ADMIN, sem enviar formulários.

Demonstrações antigas não fazem parte do host. A prévia atual é gerada em `delivery/` com dados fictícios.
