# Devxis Releases

Repositorio público de distribución de **Devxis Software** para Windows.

- Landing page: `https://alexisrr11.github.io/devxis-releases/`
- Descarga directa (siempre la última versión):
  `https://github.com/alexisrr11/devxis-releases/releases/latest/download/Devxis-Setup.exe`
- Historial de versiones: `https://github.com/alexisrr11/devxis-releases/releases`

## Qué contiene

| Archivo | Uso |
| --- | --- |
| `index.html` | Landing pública (GitHub Pages) |
| `assets/logo.png` | Logo de la marca |
| `README.md` | Este documento |

Los instaladores **no se guardan en el repositorio**: se adjuntan como archivos de cada release.

## Publicar una versión nueva

Desde el proyecto `devxis-desktop`:

```powershell
# 1. Subí la versión en package.json (por ejemplo 1.0.1)
# 2. Compilá y publicá el release
powershell -ExecutionPolicy Bypass -File .\scripts\publish-release.ps1 `
  -Notes "Correcciones en presupuestos y mejoras de rendimiento"
```

El script compila el instalador, crea el tag `v1.0.1` y sube `Devxis-Setup.exe` a este repositorio.

Si preferís hacerlo a mano:

```powershell
npm run package:win
gh release create v1.0.1 "release/Devxis-Setup.exe" `
  --repo alexisrr11/devxis-releases `
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
