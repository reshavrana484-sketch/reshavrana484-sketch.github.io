---
title: "Arquivo e formatos"
description: "Escolha entre o WXR simples do WordPress, um pacote .wxrz ou .zip e um .zip do Playground; nomes de arquivo e o que cada um contém."
translatedFrom: "3a67fd83eec60da9d979d8b0478da0fa6693c408"
---

O seletor **Formato** do rodapé tem duas opções; o nome da primeira acompanha o que vai no arquivo.

| Aparece como | Arquivo | Quando | Contém |
| --- | --- | --- | --- |
| **WXR XML** | `.xml` | Arquivos de mídia desativados e nenhuma opção | A exportação do próprio WordPress, sem mudanças |
| **WXRZ** | `.wxrz` | Arquivos de mídia ou opções | Um [pacote](../../formats/wxrz-bundle/): o WXR, a mídia, `post_content/`, `options.json` |
| **WXR ZIP** | `.zip` | Igual, com *Pacote como .zip* ativado | O mesmo [pacote como um .zip simples](../../formats/zip-bundle/) |
| **Playground** | `.zip` | Escolhido | Um [pacote de blueprint do Playground](../../formats/playground-zip/) com temas e plugins |

## Nome do arquivo

Deixe vazio para o nome de sempre do WordPress, `<site name>.WordPress.<date>` — o placeholder mostra o nome exato de hoje. Um nome digitado é sanitizado e a extensão é adicionada.

## Conteúdo como arquivos .html

Com **Configurações → Exportar → Conteúdo como arquivos .html** (ativado por padrão), o conteúdo de cada post vai para `post_content/<slug>.html` em vez de ficar dentro do WXR — fácil de ler, comparar e manter sob controle de versão. Na importação, ele é devolvido antes de o importador rodar.

## Cópias

Cada exportação feita na nova tela ou pela habilidade fica guardada como uma **cópia** por um tempo (um dia, por padrão), com um nome impossível de adivinhar, e listada em [Configurações → Cópias](../../settings/copies/).
