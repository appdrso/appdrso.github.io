# DRSO — Gestão de Voluntariedade

Host público do aplicativo do 5º CRPM. [Abrir DRSO](https://appdrso.github.io/).

`index.html` e `acesso.html` incorporam a mesma implantação Apps Script, validando origem, fonte e nonce. Dados e autenticação permanecem no aplicativo. Publicar este host não atualiza a implantação do Google Apps Script, feita manualmente pelo proprietário.

Na versão 0.8.6.1, o favicon da aba volta à imagem exata usada antes da 0.8.6.0: `assets/favicon-16-v0861.png`. `favicon.ico` contém a mesma imagem. A nova URL renova a referência do cache.

Os ícones de instalação continuam com o policial voltado à direita. O manifesto mantém imagens comuns e maskable separadas; o launcher define o recorte final. Os arquivos anteriores permanecem disponíveis para páginas em cache. Não há armazenamento offline de dados nem service worker neste host.

## Correção de abertura 0.8.6.1-r1

O acesso usa o endereço canônico com `authuser=0`. Se a página Google não iniciar o DRSO em 20 segundos, navegadores compatíveis tentam uma vez em um novo contexto sem os cookies Google existentes. A confirmação de origem, janela e nonce permanece obrigatória.

[Acesso de recuperação imediata](https://appdrso.github.io/?recuperar=1). Esse modo tem armazenamento temporário e pode pedir novo login ao recarregar. A abertura normal preserva sua sessão. Não é necessário atualizar o Apps Script para aplicar esta correção do host.
