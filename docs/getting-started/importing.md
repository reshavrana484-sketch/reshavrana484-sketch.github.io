---
title: "Importação"
description: "Como um pacote é importado com o Importador do WordPress, o que acontece com a mídia, os arquivos de conteúdo e as opções, e as outras formas de importar."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

## Com o Importador do WordPress

Envie um pacote `.wxrz` ou `.zip` em **Ferramentas → Importar → WordPress**, como qualquer arquivo WXR. Arquivos WXR compactados com gzip (`.xml.gz`) e arquivos `.xml` simples também funcionam.

Nos bastidores, antes de o importador ler qualquer coisa:

1. **O pacote é descompactado** em uma pasta privada dentro de `wp-content/uploads/eizport/tmp/<random>/`. Só os arquivos listados no manifesto são gravados, só dentro dessa pasta e só com os tipos de arquivo que o WordPress permite enviar (nunca PHP).
2. **O WXR substitui o envio**, então as verificações e etapas do próprio importador rodam como sempre.
3. **Os arquivos de conteúdo voltam ao lugar:** cada `post_content/<slug>.html` é devolvido ao seu item, pelo ID original ou, se não houver, pelo slug.
4. **A mídia é servida a partir do pacote:** quando o importador baixa um anexo, um filtro `pre_http_request` responde com o arquivo da pasta em vez da rede.
5. **As opções são aplicadas no final** (`import_end`), com cada ID de post remapeado para o post importado. Opções que apontam para itens que não foram importados ficam de fora.

A pasta é excluída quando a importação termina ou é abandonada.

## De uma cópia no site

As cópias feitas pela tela Exportar ficam listadas em **Configurações → Exporter Importer Z → Cópias**. Cada uma tem a ação **Importar**, que a importa no mesmo site — útil para restaurar conteúdo ou testar um pacote.

## Com código

- A habilidade [`eizport/import`](../../developers/abilities/#eizportimport) importa uma `copy` ou um `attachment_id` (um `.wxrz`, `.zip` ou `.xml` na biblioteca de mídia).
- [`wp eizport import <file>`](../../developers/wp-cli/) faz isso pela linha de comando.

## O que é remapeado

| No arquivo | Na importação |
| --- | --- |
| URLs dos anexos | Os arquivos vêm do pacote; o importador cria os anexos e os tamanhos de imagem como sempre |
| `post_content/<slug>.html` | Devolvido ao conteúdo do item |
| `options.json` | Definido no final; as opções listadas em `post_ids` recebem o ID do post importado |
| Produtos e suas variações, páginas e suas filhas | Importados com seus ascendentes, como faz o Importador do WordPress |
