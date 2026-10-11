---
title: "Tela Exportar"
description: "A nova tela Ferramentas → Exportar, parte por parte: a lista, os painéis laterais, o rodapé e as ações do cabeçalho."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

Ferramentas → Exportar abre uma tela construída como as telas mais novas do painel do WordPress (DataViews e DataForm, sobre o framework de telas do painel do core). Ela usa as [abilities](../../developers/abilities/) do plugin, então a tela, a REST e os agentes de IA exportam do mesmo jeito.

![A tela Exportar com Páginas (1 item), Produtos (filtrado) e Opções (Página inicial + Básicas) marcados.](../../../assets/screenshots/export-screen.webp)

## A lista

Uma linha para cada coisa que pode ser exportada:

- **Tipos de conteúdo** — Posts, Páginas, Produtos, Pedidos, Cupons, Formulários e qualquer tipo de post personalizado com tela no painel. Os filhos vão junto com os ascendentes (as variações de um produto).
- **Anexos** — itens de mídia, escolhidos diretamente.
- **Opções** — configurações do site ([mais](../options/)).

A coluna **Exportar** diz o que vai: *Não incluído*, *Tudo*, *Filtrado*, *3 itens* ou, em Opções, *Página inicial + Básicas*. **Nada marcado exporta todo o conteúdo**, como faz o WordPress.

As ações de cada linha: **Escolher itens** (abre o painel lateral), **Exportar tudo** e **Não exportar**. Marque várias linhas para agir sobre todas de uma vez.

## O painel lateral

Clicar em uma linha abre os itens dela em um painel à direita ([escolher itens](../choosing-items/)). A URL do painel pode ser compartilhada: `…&p=/export?type=page`.

## O rodapé

As configurações do arquivo ficam embaixo:

| Campo | O que faz |
| --- | --- |
| **Formato** | *WXR XML* (o arquivo simples do WordPress), *WXRZ* ou *WXR ZIP* (um pacote, assim que arquivos de mídia ou configurações vão junto) ou *Playground* ([formatos](../file-and-formats/)) |
| **Nome do arquivo** | Vazio: o nome de sempre do WordPress, `<site>.WordPress.<date>`, mostrado como placeholder |
| **Arquivos de mídia** | Coloca os arquivos dos anexos exportados dentro do pacote |
| **Opções** | Temas e plugins do Playground (habilitado com o formato Playground) |

## Ações do cabeçalho

- **Salvar como padrão** — guarda as escolhas atuais para começar com elas da próxima vez ([padrões salvos](../saved-defaults/)).
- **Exportar** — grava o arquivo como uma [cópia](../../settings/copies/) e oferece o download.

## No celular

A lista mostra só a coluna de título, com o que é exportado embaixo; o rodapé fica empilhado; o painel lateral ocupa a tela.
