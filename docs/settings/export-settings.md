---
title: "Configurações de exportação"
description: "Configurações → Exporter Importer Z → Exportar — mídia anexada, configurações vinculadas, pacotes .zip e conteúdo como arquivos .html."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

![Configurações → Exporter Importer Z → Exportar.](../../../assets/screenshots/settings-export.webp)

Tudo em um cartão, **Com os itens exportados**:

| Configuração | Padrão | Por exportação (`eizport/export`) |
| --- | --- | --- |
| **Só mídia anexada** — os itens trazem só a mídia anexada e as imagens destacadas, como faz o WordPress, não a mídia usada no conteúdo ([mídia](../../exporting/media/)) | Desativado | `media_used` |
| **Configurações vinculadas** — quando vêm junto as configurações que apontam para os itens exportados: quando os itens são marcados e na exportação, quando marcados, na exportação, nunca ([opções](../../exporting/options/#linked-settings)) | Ambos | `options.linked` |
| **Pacote como .zip** — os pacotes são `.zip` simples em vez de `.wxrz` ([pacote ZIP](../../formats/zip-bundle/)) | Desativado | `zip` |
| **Conteúdo como arquivos .html** — o conteúdo de cada post em `post_content/<slug>.html` | Ativado | `post_content` |
