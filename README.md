# ProLobby.com — espelho

Espelho automático de [`ljborgess/ProLobby.com`](https://github.com/ljborgess/ProLobby.com), o repositório original do projeto.

O código está nas branches [`dev`](../../tree/dev) (onde o produto é construído) e [`main`](../../tree/main). Elas são cópias do original e voltam ao estado dele a cada sincronização.

## Como funciona

- O workflow `mirror-upstream` roda a cada 30 minutos e sob demanda (aba **Actions** > **Mirror upstream** > **Run workflow**).
- Ele copia todas as branches e tags do original para cá. Branches são atualizadas à força, para seguir o original.
- Nada é apagado: uma branch que sumiu do original continua aqui.
- Esta branch (`mirror-sync`) é a padrão e nunca é sobrescrita. O arquivo do workflow só funciona se estiver nela.

## Regras de uso

- **Não faça commit direto em branch que existe no original** (`main`, `dev`, `feat/...`). A próxima sincronização sobrescreve. Trabalhe em branches com nome próprio e abra o PR para `dev` do original.
- O espelho depende do segredo `MIRROR_PUSH_TOKEN` (**Settings > Secrets and variables > Actions**): um token de acesso pessoal fine-grained, só para este repositório, com **Contents: Read and write** e **Workflows: Read and write**.
- O GitHub desativa workflows agendados em repositório público sem atividade por 60 dias. Se isso acontecer, reative em **Actions**.
