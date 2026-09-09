# lysi-oauth — pont HTTPS Notion → Lysi

Page statique **publique** pour le redirect OAuth Notion. Aucun secret, aucun cookie, aucune analytics.

Notion n’accepte que des redirect `https`. Lysi écoute `dumpit://notion-oauth` (et `dumpit-dev://` pour Dev). Cette page fait le hop.

L’app iOS reste privée : [`Zoliandru/dumpit-ios`](https://github.com/Zoliandru/dumpit-ios).

## URLs à coller chez Notion

Après activation de GitHub Pages :

```
https://zoliandru.github.io/lysi-oauth/notion-oauth.html
https://zoliandru.github.io/lysi-oauth/notion-oauth-dev.html
```

| Fichier | Ouvre |
| --- | --- |
| `notion-oauth.html` | `dumpit://notion-oauth?…` (Lysi) |
| `notion-oauth-dev.html` | `dumpit-dev://notion-oauth?…` (Lysi Dev) |

Query `code`, `state` (et `error`) sont recopiées telles quelles.

## Activer GitHub Pages

1. Ce repo doit rester **public**.
2. GitHub → **Settings** → **Pages**.
3. **Build and deployment** → Source = **Deploy from a branch**.
4. Branch = `main`, dossier = `/` (root). Save.
5. Attendre 1–2 min. Vérifier les 2 URLs ci-dessus (sans query : message « Ouverture… » + lien).

Si le compte GitHub n’est pas `Zoliandru`, l’URL devient `https://<user>.github.io/lysi-oauth/…`. Coller alors ces URLs dans Notion **et** dans `Config/NotionOAuth.xcconfig` de dumpit-ios.

## Checklist fondateur

1. Pousser ce repo, activer Pages, noter les 2 URLs https.
2. Notion → intégration **Public** → Redirect URIs = ces 2 https **exactes**. Supprimer `dumpit://` et `https://notion-oauth`.
3. Dans dumpit-ios : `Config/NotionOAuth.xcconfig` (gitignoré) = `client_id`, `client_secret`, et les redirect https seulement si le host Pages n’est pas `zoliandru.github.io`.
4. Xcode : Use Version on Disk → Clean → Run → Identifiants → **Connecter avec Notion** → autoriser → retour Lysi → bases listées.

## Hors périmètre

- Pas de `client_secret` ici (l’échange de jeton reste dans l’app).
- Pas d’Universal Links.
- Pas de code DumpIt / Lysi.
