# tetis-oauth — pages publiques Tetis (GitHub Pages)

Repo **public** : pont HTTPS OAuth (Notion / GitHub) + pages légales (confidentialité, support, conditions). Aucun secret, aucun cookie, aucune analytics.

L’app iOS reste privée : [`Zoliandru/dumpit-ios`](https://github.com/Zoliandru/dumpit-ios).

Ancien nom : `lysi-oauth`. Les URL `zoliandru.github.io/lysi-oauth/…` ne sont plus valides.

## Pages légales

```
https://zoliandru.github.io/tetis-oauth/
https://zoliandru.github.io/tetis-oauth/privacy.html
https://zoliandru.github.io/tetis-oauth/support.html
https://zoliandru.github.io/tetis-oauth/terms.html
```

Contact : `tetis.app@icloud.com`

## Pont OAuth

Notion et GitHub n’acceptent que des redirect `https`. Tetis écoute `dumpit://notion-oauth` / `dumpit://github-oauth` (et `dumpit-dev://` pour Dev). Ces pages font le hop.

```
https://zoliandru.github.io/tetis-oauth/notion-oauth.html
https://zoliandru.github.io/tetis-oauth/notion-oauth-dev.html
https://zoliandru.github.io/tetis-oauth/github-oauth.html
https://zoliandru.github.io/tetis-oauth/github-oauth-dev.html
```

| Fichier | Ouvre |
| --- | --- |
| `notion-oauth.html` | `dumpit://notion-oauth?…` |
| `notion-oauth-dev.html` | `dumpit-dev://notion-oauth?…` |
| `github-oauth.html` | `dumpit://github-oauth?…` |
| `github-oauth-dev.html` | `dumpit-dev://github-oauth?…` |

Query `code`, `state` (et `error`) sont recopiées telles quelles.

## Chez Notion / GitHub

Redirect / callback = les 4 URL https **exactes** ci-dessus. Pas de `dumpit://` dans les portails.

## Hors périmètre

- Pas de `client_secret` ici (l’échange de jeton reste dans l’app).
- Pas d’Universal Links.
- Pas de code DumpIt / Tetis iOS.
