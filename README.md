# Danillo App Store

Loja comunitária do [umbrelOS](https://umbrel.com) com os meus apps, no formato da [umbrel-community-app-store](https://github.com/getumbrel/umbrel-community-app-store).

No Umbrel: App Store › ⋯ › Community App Stores › cole `https://github.com/danillo-ao/umbrel-store`.

| App | Pasta | Código |
|---|---|---|
| homesync | [danillo-homesync](danillo-homesync) | [danillo-ao/homesync](https://github.com/danillo-ao/homesync) |
| firelink | [danillo-firelink](danillo-firelink) | [danillo-ao/firelink](https://github.com/danillo-ao/firelink) |

## Estrutura

O umbrelOS lê só o `umbrel-app-store.yml` e as pastas `*/umbrel-app.yml` da raiz:

```
umbrel-app-store.yml          # loja "danillo": prefixo obrigatório do id de todo app dela
danillo-<app>/                # pasta = id do app
├── umbrel-app.yml            # ficha do app na App Store do Umbrel
├── docker-compose.yml        # app_proxy + serviços (imagens já publicadas)
├── icon.png
└── data/.gitkeep             # faz o Umbrel criar a pasta de dados (dono 1000) na instalação
```

Cada `.gitkeep` vira uma pasta do app criada com dono 1000; o firelink usa várias (`data/docker`,
`data/firelink`, `data/stacks` e `run`).

## Nova versão de um app

Publique a imagem nova no repositório do app e só então atualize, aqui na `main`, a tag da imagem no `docker-compose.yml` e `version`/`releaseNotes` no `umbrel-app.yml`. O Umbrel oferece a atualização quando a `version` muda.
