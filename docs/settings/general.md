---
title: "Geral"
description: "Configurações → Exporter Importer Z → Geral — a tela Exportar, os padrões salvos e por quanto tempo as cópias são mantidas."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

![Configurações → Exporter Importer Z → Geral.](../../../assets/screenshots/settings-general.webp)

## Tela Exportar

| Configuração | Padrão | |
| --- | --- | --- |
| **Usar a tela Exportar clássica** | Desativado | Ferramentas → Exportar abre a tela do próprio WordPress com as opções do plugin, em vez da nova ([tela clássica](../../exporting/classic-screen/)) |
| **Os padrões são salvos para** | Cada usuário | Ou *O site inteiro* ([padrões salvos](../../exporting/saved-defaults/)) |

*Limpar padrões salvos* os esquece (os do usuário atual ou os do site).

## Cópias

**Manter cópias por**: 1 hora, 12 horas, **1 dia** (padrão), 1 semana ou até serem excluídas. Depois disso, a cópia deixa de ser servida e é excluída por um evento do cron (e no próximo uso, onde o cron não roda). As cópias já guardadas também seguem uma nova escolha. Desenvolvedores podem mudar isso com [`eizport_copy_lifetime`](../../developers/hooks/#eizport_copy_lifetime).

## Quem pode mudá-las

As configurações exigem `manage_options`. A página em si abre para qualquer pessoa que possa exportar (para ver as cópias).
