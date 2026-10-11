# Exporter Importer Z — pt-BR

Tradução em português do Brasil do site do [Exporter Importer Z](https://github.com/eizport/exporter-importer-z): https://eizport.github.io/pt-br/.

Este repositório só tem texto traduzido. O site é montado no repositório do plugin, que baixa esta tradução a cada publicação (veja `site/translations.json` e `site/scripts/translations.mjs` lá). Um push aqui publica o site de novo.

## O que há aqui

| Caminho | O quê |
| --- | --- |
| `strings.json` | Os textos das páginas e dos componentes do site (menus, botões, landing, doações). Mesmo formato de `site/src/i18n/en.ts` do repositório do plugin; o que faltar aparece em inglês. |
| `docs/<grupo>/<página>.md` | A documentação: mesmo caminho e nome da página em inglês em `site/src/content/docs/`. |
| `GLOSSARIO.md` | Os termos usados, iguais no site, na documentação e no plugin. |
| `assets/screenshots/` | (em breve) Screenshots da interface em português, com os mesmos nomes dos em inglês. |
| `languages/` | (em breve) A tradução do plugin, `exporter-importer-z-pt_BR.po`. |

## Como traduzir uma página

1. Copie a página em inglês de `site/src/content/docs/<grupo>/<página>.md` para `docs/<grupo>/<página>.md`.
2. Traduza `title`, `description` e o texto, seguindo o `GLOSSARIO.md`. Não mude código, nomes de arquivos, URLs, alvos de links nem caminhos de imagens.
3. Em `translatedFrom`, ponha o commit do repositório do plugin de onde a página em inglês foi copiada.

Quando a página em inglês muda depois desse commit, o site mostra um aviso de que a tradução está desatualizada. Atualize o texto e o `translatedFrom`. Uma página que ainda não existe aqui aparece em inglês, com um link para traduzi-la.

## Ver localmente

No repositório do plugin, com este ao lado:

```sh
cd site
npm run translations -- --local pt-br=../../exporter-importer-z-pt-br
npm run dev   # http://localhost:4321/pt-br/
```
