---
title: "Opções"
description: "Exporte as configurações do site uma a uma, por grupo ou todas de uma vez; configurações vinculadas; o que nunca é exportado; como os IDs são remapeados."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

A linha **Opções** exporta as configurações do site num `options.json` dentro do pacote, definidas no outro site quando a importação termina.

![O painel Opções, filtrado pelo grupo sugerido Básicas.](../../../assets/screenshots/options-panel.webp)

## Três formas de escolher

- **Uma a uma** — todas as opções que o site tem (pesquisa, páginas), cada uma com o tamanho e um selo *IDs remapeados na importação* quando guarda um ID de post.
- **Por grupo** — filtre o painel por um grupo e exporte-o: **Básicas** (sugeridas), Leitura, Geral, Links permanentes, Discussão, Mídia, Privacidade, Personalizações do tema, Páginas do WooCommerce. Um grupo é resolvido quando o arquivo é gerado, então acompanha o tema ativo.
- **Todas** — todas as opções que podem ser exportadas.

As opções marcadas têm prioridade sobre o filtro de grupo. Sem nada escolhido ainda, o painel abre em **Básicas**: título, descrição, idioma, fuso horário, formatos de data, página inicial e página de posts, posts por página, links permanentes, personalizações do tema e ícone do site.

<a id="linked-settings"></a>
## Configurações vinculadas

Algumas opções apontam para um post: `page_on_front`, `page_for_posts`, `wp_page_for_privacy_policy`, `site_icon`, os IDs de página do WooCommerce. Quando o post é exportado, essas opções podem vir junto — com as que elas precisam, como `show_on_front`:

| Modo (Configurações → Exportar) | Quando |
| --- | --- |
| **Quando itens são marcados, e na exportação** (padrão) | Na hora, na linha Opções, quando você marca um item com uma função, e de novo quando o arquivo é gerado — para itens exportados por filtros ou com todo o conteúdo |
| **Quando itens são marcados** | Só pela seleção do painel lateral |
| **Na exportação** | Só quando o arquivo é gerado |
| **Nunca** | Você escolhe cada opção |

## Nunca exportadas

URLs do site (`siteurl`, `home`), o e-mail do administrador, chaves e salts, `active_plugins`, funções (`<prefix>user_roles`), `cron`, `rewrite_rules`, versões do banco de dados, credenciais do servidor de e-mail, as próprias configurações do plugin e todos os transients. Plugins acrescentam as suas com [`eizport_denied_options`](../../developers/hooks/#eizport_denied_options); as do próprio WordPress não podem ser removidas.

## IDs na importação

O `options.json` lista, em `post_ids`, as opções que guardam um ID de post. Na importação, cada uma recebe o ID que o importador deu a esse post; se o post não foi importado, a opção fica de fora em vez de apontar para a coisa errada. Os valores de `theme_mods_<theme>` também são remapeados (logo, menus).
