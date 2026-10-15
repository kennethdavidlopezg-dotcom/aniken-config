# aniken-config

Configuración remota y versiones publicadas de **Aniken** (app Android).

- `config.json` — dominios, patrones de extracción, servidores desactivados,
  avisos y la última versión disponible. La app la descarga cada pocas horas.
- `config.json.sig` — firma Ed25519 de `config.json`. La app rechaza cualquier
  configuración que no esté firmada con la clave del autor, así que editar este
  repositorio sin esa clave no afecta a nadie.
- **Releases** — los APK de cada versión, uno por arquitectura.

No edites `config.json` sin volver a firmarlo: usa `tool/publish_config.ps1`
desde el proyecto de la app.

## Campos de `config.json`

| Campo | Para qué |
|---|---|
| `revision` | Sube en cada cambio; la app nunca aplica una revisión más antigua. |
| `domains.jkanime`, `domains.tioanime` | Dominio actual de cada web. |
| `backupSources` | `false` desactiva TioAnime como respaldo. |
| `aniskip` | `false` desactiva los saltos de intro/créditos. |
| `disabledServers` | Servidores que no se prueban, como `"jkanime:Magi"`. |
| `patterns` | Sustituye expresiones regulares de extracción (`jk.videoIframe`, `jk.serversArray`, `tio.videos`, `media.quoted`…). |
| `notice` | `{ "id": "…", "text": "…" }` muestra un aviso una vez. |
| `update` | Lo rellena `tool/publish_release.ps1` al publicar una versión. |
