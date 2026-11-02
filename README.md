# Devxis Releases

Repositorio público de distribución de **Devxis Software** para Windows.

- Landing page: `https://alexisrr11.github.io/DVX-software-exe/`
- Descarga directa (siempre la última versión):
  `https://github.com/alexisrr11/DVX-software-exe/releases/latest/download/Devxis-Setup.exe`
- Historial de versiones: `https://github.com/alexisrr11/DVX-software-exe/releases`

## Qué contiene

| Archivo | Uso |
| --- | --- |
| `index.html` | Landing pública (GitHub Pages) |
| `assets/logo.png` | Logo de la marca |
| `README.md` | Este documento |

Los instaladores **no se guardan en el repositorio**: se adjuntan como archivos de cada release.

## Activar GitHub Pages (una sola vez)

1. Repo → **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: **main**, carpeta **/ (root)**
4. **Save**

En uno o dos minutos la landing queda publicada en `https://alexisrr11.github.io/DVX-software-exe/`.

## Publicar una versión nueva

Desde el proyecto `devxis-desktop`:

```powershell
# 1. Subí "version" en package.json (por ejemplo 1.0.1)
# 2. Autenticá GitHub CLI una sola vez: gh auth login
# 3. Compilá y publicá el release
powershell -ExecutionPolicy Bypass -File .\scripts\publish-release.ps1 `
  -Notes "Correcciones en presupuestos y mejoras de rendimiento"
```

El script compila el instalador, crea el tag `v1.0.1` y sube `Devxis-Setup.exe` a este repositorio.

Si preferís hacerlo a mano:

```powershell
npm run package:win
gh release create v1.0.1 "release/Devxis-Setup.exe" `
  --repo alexisrr11/DVX-software-exe `
  --title "Devxis Software 1.0.1" `
  --notes "Descripción de los cambios"
```

> El nombre del archivo debe ser siempre `Devxis-Setup.exe` para que el enlace
> `/releases/latest/download/Devxis-Setup.exe` de la landing siga funcionando.

## Requisito importante

La landing enlaza a `/releases/latest/download/...`, que GitHub resuelve al último
release **publicado** (no borrador y no marcado como *pre-release*).

## Actualizar la landing

```powershell
git add .
git commit -m "Actualizar landing"
git push origin main
```

GitHub Pages se actualiza solo en uno o dos minutos.
