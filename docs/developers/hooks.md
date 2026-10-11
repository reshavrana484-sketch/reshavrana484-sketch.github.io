---
title: "Hooks"
description: "Cada filtro e ação do Exporter Importer Z, com seus parâmetros e um exemplo."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

Todos os hooks têm o prefixo `eizport_`. Adicione-os a partir de um plugin ou do `functions.php` de um tema.

## eizport_linked_options

Opções que apontam para um post, com a função que dão a ele. Elas recebem o ID do post importado na importação, aparecem como um selo no item e podem ir junto com ele ([configurações vinculadas](../../exporting/options/#linked-settings)).

```php
add_filter( 'eizport_linked_options', function ( array $linked ) {
	$linked['my_plugin_landing_page'] = array(
		'label' => __( 'Landing page', 'my-plugin' ),     // The role, shown as a badge.
		'with'  => array( 'my_plugin_landing_enabled' ),  // Options that go with it.
		'when'  => array( 'my_plugin_mode' => 'landing' ), // Only while these hold these values.
	);
	return $linked;
} );
```

| Parâmetro | |
| --- | --- |
| `array $linked` | Nome da opção → `label` (string), `with` (string[], opcional), `when` (opção → valor, opcional) |

## eizport_option_groups

Os grupos de opções oferecidos nas telas e em `options.groups`.

```php
add_filter( 'eizport_option_groups', function ( array $groups ) {
	$groups['my-plugin'] = array(
		'label'   => __( 'My Plugin: layout and colors', 'my-plugin' ), // "Name: what it holds".
		'options' => array( 'my_plugin_layout', 'my_plugin_colors' ),
	);
	return $groups;
} );
```

## eizport_denied_options

Mais opções que nunca são exportadas — chaves, tokens, licenças, números de versão. Retorna nomes a **adicionar**; as opções negadas do próprio WordPress não podem ser removidas.

```php
add_filter( 'eizport_denied_options', function ( array $names ) {
	return array_merge( $names, array( 'my_plugin_api_key', 'my_plugin_db_version' ) );
} );
```

## eizport_media_used

Anexos que um post usa além dos que o conteúdo cita, como uma galeria guardada em meta. Roda quando alguns itens são exportados e *Só mídia anexada* está desativada.

```php
add_filter( 'eizport_media_used', function ( array $used, WP_Post $post ) {
	if ( 'portfolio' === $post->post_type ) {
		$used = array_merge( $used, wp_parse_id_list( get_post_meta( $post->ID, 'gallery', true ) ) );
	}
	return $used;
}, 10, 2 );
```

## eizport_register_compat

Ação, em `plugins_loaded` (prioridade 20), onde as compatibilidades conectam os filtros acima. Veja [compatibilidades](../compatibilities/).

## eizport_post_id_options

Opções que guardam um ID de post, mapeadas na importação. Por padrão, as chaves de `eizport_linked_options`; mantido por compatibilidade.

| Parâmetro | |
| --- | --- |
| `string[] $names` | Nomes das opções |

## eizport_post_content

O conteúdo que um item importado recebe do seu arquivo em `post_content/`.

| Parâmetro | |
| --- | --- |
| `string\|null $content` | O conteúdo do arquivo, ou `null` quando não há |
| `array $item` | `id` (ID original), `type`, `slug` |
| `string $dir` | Pasta em que o pacote foi desempacotado |

## eizport_wxrz_max_bytes

O máximo que um pacote pode ocupar ao ser expandido na importação. Padrão `512 * MB_IN_BYTES`.

## eizport_playground_blueprint

O blueprint de um `.zip` do Playground, antes de ser gravado.

| Parâmetro | |
| --- | --- |
| `array $blueprint` | O blueprint (`steps`, `landingPage`…) |
| `string $wxr_name` | O nome do WXR dentro do `.zip` |

## eizport_selection_limit

Quantos itens cada lista *Por seleção* da tela clássica mostra (os mais recentes). Padrão `1000`.

## eizport_copy_lifetime

Quanto tempo uma cópia dura, em segundos; `0` mantém as cópias até serem excluídas. Padrão: o escolhido em Configurações.
