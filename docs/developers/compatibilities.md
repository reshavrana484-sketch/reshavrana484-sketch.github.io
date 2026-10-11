---
title: "Compatibilidades"
description: "Como o suporte a outros plugins é feito com os hooks públicos, com o do WooCommerce como exemplo, e como um plugin traz o seu próprio."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

O suporte a outro plugin é uma **compatibilidade**: um arquivo que usa só os [hooks](../hooks/) públicos. O plugin traz uma, para o WooCommerce; qualquer plugin pode adicionar a sua — ou substituir a que vem incluída.

## A compatibilidade com o WooCommerce

`includes/compat/woocommerce.php`, registrada em `eizport_register_compat` quando `WooCommerce` existe:

| Hook | Adiciona |
| --- | --- |
| `eizport_linked_options` | Página da loja, Página do carrinho, Página de finalização de compra, Página Minha conta e Página de termos e condições, como funções |
| `eizport_option_groups` | O grupo *Páginas do WooCommerce* |
| `eizport_denied_options` | `woocommerce_version`, `woocommerce_db_version` |
| `eizport_media_used` | Galerias de produtos e variações (`_product_image_gallery`) |

## Como escrever uma

```php
add_action( 'eizport_register_compat', function () {
	if ( ! class_exists( 'My_Plugin' ) ) {
		return;
	}
	add_filter( 'eizport_linked_options', 'my_plugin_eizport_linked' );
	add_filter( 'eizport_option_groups', 'my_plugin_eizport_groups' );
	add_filter( 'eizport_denied_options', 'my_plugin_eizport_denied' );
} );
```

`eizport_register_compat` é disparado em `plugins_loaded` com prioridade 20, depois que todos os plugins carregaram, então as verificações com `class_exists()` são confiáveis.

## Como substituir a incluída

Um plugin que traz o seu próprio suporte remove primeiro o que vem incluído:

```php
remove_action( 'eizport_register_compat', 'ExporterImporterZ\Compat\WooCommerce\register' );
```

## Testes

Teste as funções da compatibilidade diretamente, para que os testes passem sem o outro plugin instalado, e verifique que ela só se registra quando esse plugin está ativo.
