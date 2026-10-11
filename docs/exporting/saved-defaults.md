---
title: "Padrões salvos"
description: "Salve as escolhas da tela Exportar como padrão, por usuário ou para o site inteiro, nas duas telas."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

**Salvar como padrão** guarda tudo o que você escolheu: tipos de conteúdo com seus itens ou filtros, opções, formato, nome do arquivo, arquivos de mídia e os temas e plugins do Playground. Uma nova sessão do navegador começa com eles.

## De quem são os padrões

**Configurações → Geral → Os padrões são salvos para**:

- **Cada usuário** (padrão) — guardados nos metadados do usuário; quem pode exportar salva os seus.
- **O site inteiro** — um conjunto para todos; salvar ou limpar exige `manage_options`.

## As duas telas

- **Tela nova:** *Salvar como padrão* no cabeçalho (o aviso oferece *Limpar*).
- **Tela clássica:** marque *Salvar estas escolhas como meu padrão* antes de baixar. A tela clássica também já começa preenchida com os padrões.

## Limpar

*Limpar padrões salvos* em Configurações → Geral, ou a ability [`eizport/clear-export-defaults`](../../developers/abilities/#defaults).

## O que é verificado

Os padrões são sanitizados ao salvar e de novo ao carregar: tipos e itens desconhecidos, opções que nunca são exportadas e temas ou plugins que não estão mais instalados são descartados. Os filtros guardam só os valores definidos.
