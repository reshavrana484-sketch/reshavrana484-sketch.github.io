---
title: "Escolher itens"
description: "Por filtros ou por seleção, por tipo de conteúdo, no painel lateral; filhos, anexos e funções."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

Cada tipo de conteúdo é exportado **por filtros** ou **por seleção**, de forma independente.

![O painel Páginas: uma caixa de seleção por página, funções como selos.](../../../assets/screenshots/items-panel.webp)

## Por seleção

Marque os itens a exportar. A seleção sobrevive à pesquisa e à paginação: marque alguns na página 1, pesquise, marque mais. O botão principal diz quantos: **Exportar 3 itens**.

## Por filtros

Sem nada marcado, os filtros do painel decidem: status, autor, datas e cada taxonomia (categorias de produtos, tags…). O botão mostra **Exportar os itens filtrados**; sem filtro, **Exportar tudo de Páginas**.

> **Itens marcados vencem os filtros.** A mesma regra vale para o painel Opções.

## O que vai junto

| Com | Vai junto |
| --- | --- |
| Qualquer item | Sua mídia anexada e sua imagem destacada (o WordPress faz isso) |
| Qualquer item | A mídia usada no conteúdo sem estar anexada ([mídia](../media/)) |
| Um produto | Suas variações e suas avaliações |
| Uma página | Suas páginas filhas só se também corresponderem — selecione ou filtre-as |
| Um item com uma função | As configurações que apontam para ele ([configurações vinculadas](../options/#linked-settings)) |

## Funções

Itens para os quais uma configuração aponta mostram um selo: **Página inicial**, **Página de posts**, **Página de política de privacidade**, **Ícone do site** e as páginas que os plugins registram, como a **Página da loja**, a **Página do carrinho**, a **Página de finalização de compra**, a **Página Minha conta** e a **Página de termos e condições** do WooCommerce. Os plugins adicionam as suas com [`eizport_linked_options`](../../developers/hooks/#eizport_linked_options).

## Limites

A tela clássica lista os 1.000 itens mais recentes por tipo (filtro [`eizport_selection_limit`](../../developers/hooks/#eizport_selection_limit)); a nova tela pagina por todos eles.
