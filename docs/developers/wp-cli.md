---
title: "WP-CLI"
description: "Importe pacotes pela linha de comando com wp eizport import e rode as abilities com wp eval."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

## wp eizport import

Importa um pacote `.wxrz` ou `.zip`, um WXR compactado com gzip (`.xml.gz`) ou um `.xml` simples com o Importador do WordPress — a mídia vem do pacote, os arquivos de `post_content/` voltam para o conteúdo e as opções são definidas no final.

```bash
wp eizport import site.wxrz --user=admin
```

| Argumento | |
| --- | --- |
| `<file>` | O arquivo a importar |
| `--user=<login>` | A quem os posts são atribuídos; padrão: o primeiro administrador |

Ele precisa do plugin Importador do WordPress instalado (não precisa estar ativo).

## Exportar pela linha de comando

Rode a ability [`eizport/export`](../abilities/#eizportexport):

```bash
wp eval '
wp_set_current_user( 1 );
$copy = wp_get_ability( "eizport/export" )->execute( array(
	"types"   => array( "page" => array( "ids" => array( 43 ) ) ),
	"options" => array( "groups" => array( "basics" ) ),
) );
echo is_wp_error( $copy ) ? $copy->get_error_message() : $copy["download_url"];
'
```

A cópia fica em `wp-content/uploads/eizport/tmp/`; uma exportação por processo `wp`.

## Outras abilities

Qualquer ability funciona do mesmo jeito: `wp_get_ability( 'eizport/get-copies' )->execute()`, `wp_get_ability( 'eizport/delete-copies' )->execute( array( 'all' => true ) )`…
