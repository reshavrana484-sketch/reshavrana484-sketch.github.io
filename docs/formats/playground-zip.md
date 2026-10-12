---
title: ".zip do Playground"
description: "Um pacote de blueprint do WordPress Playground que inicia um site com o conteúdo, a mídia, o tema e os plugins exportados — como é montado e como executá-lo."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

Com o formato **Playground**, a exportação é um `.zip` pronto para o [WordPress Playground](https://wordpress.org/playground/): um pacote de blueprint que instala os temas e plugins que você escolheu e importa o conteúdo.

![Opções do Playground: os temas e plugins que o .zip instala.](../../../assets/screenshots/playground-options.webp)

## Execute

```bash
npx @wp-playground/cli@latest server --blueprint=./site.zip
```

Ou abra o link dele no playground.wordpress.net (nova tela: a ação **Abrir no Playground** em [Cópias](../../settings/copies/); tela clássica: *Manter uma cópia para abrir por link*). A cópia é servida com os cabeçalhos CORS de que o Playground precisa.

**Mesmo de um servidor local.** O Playground roda no seu navegador, então uma cópia feita no WordPress Studio ou em qualquer site `localhost` abre no playground.wordpress.net sem ser enviada a lugar nenhum — o navegador a coleta da sua máquina (o link só funciona no seu computador).

## Temas e plugins

Qualquer tema ou plugin **instalado** pode entrar — do diretório do WordPress.org ou não: premium, personalizado, interno. Eles são compactados a partir do site dentro do pacote, e o Playground os instala dali.

> **Use com responsabilidade.** Temas e plugins premium e personalizados são copiados para dentro do arquivo. Compartilhe um `.zip` do Playground só onde as licenças deles permitem — guarde os de licença paga para você ou sua equipe.

## Dentro

```text
blueprint.json
<site>.WordPress.<date>.xml        the plain WXR (content inside, not in post_content/)
uploads/…                          media files, when Media files is on
post_content/…                     content files, when Content as .html files is on
themes/<stylesheet>.zip            each theme chosen (a child brings its parent)
plugins/<slug>.zip                 each plugin chosen
```

## O que o blueprint faz

1. Instala os temas (os ascendentes primeiro) e ativa o tema ativo, se escolhido, senão o primeiro.
2. Instala e ativa os plugins.
3. Grava os arquivos de mídia e de conteúdo e dois plugins obrigatórios temporários: um responde com os arquivos quando o importador baixa a mídia e devolve cada `.html` ao seu post (`wp_import_post_data_raw`); o outro define as opções quando a importação termina, com os IDs remapeados.
4. Executa `importWxr` (o próprio Playground instala o Importador do WordPress).
5. Remove os plugins e arquivos temporários.

O filtro [`eizport_playground_blueprint`](../../developers/hooks/#eizport_playground_blueprint) altera o blueprint antes de ele ser gravado.
