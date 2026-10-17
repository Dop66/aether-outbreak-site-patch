# aether-outbreak-site-patch

Site de notícias e notas de atualização do Aether Outbreak, publicado pelo
GitHub Pages em <https://dop66.github.io/aether-outbreak-site-patch/>.

O launcher lê o **`noticias.json`** deste site
(<https://dop66.github.io/aether-outbreak-site-patch/noticias.json>) e mostra
as notícias com o visual dele. Atualizou o site, o launcher mostra sozinho
(o Pages guarda cache de uns 10 minutos).

## Publicar uma notícia

Crie um arquivo em `_posts/` com o nome `AAAA-MM-DD-titulo-curto.md`:

```markdown
---
title: Título da notícia
tag: atualização        # atualização, aviso, evento ou novidade (padrão)
versao: "2.3.0"         # opcional: versão do jogo (com aspas)
destaque: true          # opcional: fica em destaque no launcher
imagem: /assets/img/capa.png   # opcional: imagem em assets/img/
resumo: Uma ou duas frases que aparecem no card do launcher.
---

Texto completo em Markdown (## títulos, - listas, **negrito**, [links](...)).
```

Dê commit e push na branch `main`. O GitHub Pages monta a página da notícia e
o `noticias.json` sozinho, sem precisar instalar nada.

- Sem `resumo`, o card usa o primeiro parágrafo do texto.
- Para esconder uma notícia sem apagar, ponha `published: false`.
- O `noticias.json` leva as 20 mais novas (`noticias_no_launcher` no `_config.yml`).

## Formato do `noticias.json` (o que o launcher lê)

```json
{
  "formato": 1,
  "site": "Aether Outbreak",
  "atualizado": "2026-10-17T20:00:00-03:00",
  "noticias": [
    {
      "id": "/2026/10/17/versao-2-2-0",
      "titulo": "Versão 2.2.0: ...",
      "data": "2026-10-17T00:00:00-03:00",
      "tag": "atualização",
      "versao": "2.2.0",
      "destaque": false,
      "resumo": "...",
      "imagem": "https://dop66.github.io/aether-outbreak-site-patch/assets/img/capa.png",
      "link": "https://dop66.github.io/aether-outbreak-site-patch/noticias/2026/10/17/versao-2-2-0/"
    }
  ]
}
```

`versao` e `imagem` podem vir `null`. Se um campo novo for criado, suba o
`formato` só quando o launcher antigo deixar de entender o arquivo.

## Ativar o GitHub Pages (uma vez)

No repositório: **Settings → Pages → Build and deployment → Source: Deploy
from a branch → Branch: `main` / `(root)`**.
