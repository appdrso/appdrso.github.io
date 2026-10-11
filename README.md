# DRSO — Gestão de Voluntariedade

Host público do aplicativo do 5º CRPM. [Abrir DRSO](https://appdrso.github.io/).

`index.html` e `acesso.html` incorporam a mesma implantação Apps Script, validando origem, fonte e nonce. Dados e autenticação permanecem no aplicativo.

A auditoria 0.8.5.5 sincronizou os dois pontos de entrada e removeu prévias antigas e ícones sem referência. Publicar este host não atualiza o código da implantação Apps Script.

A rodada visual 0.8.6.0 padroniza os ícones com o policial voltado à direita. O manifesto declara ícones comuns e maskable separadamente; o launcher define o recorte final. O ícone v067 permanece para compatibilidade com páginas em cache. Não há armazenamento offline de dados nem service worker neste host.
