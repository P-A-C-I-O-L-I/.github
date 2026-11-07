# P A C I O L I · `.github`

Repositorio especial de la organización. GitHub aplica su contenido como valor por defecto a **todos** los repositorios de P A C I O L I que no definan sus propios archivos equivalentes.

## Regla de este repositorio

**Este repositorio es público**, porque GitHub solo aplica las plantillas de la organización desde un repositorio `.github` público. Por eso aquí solo existen plantillas, reglas de proceso y workflows genéricos.

Nunca entra a este repositorio: código de producto, datos, nombres de clientes, detalles de la arquitectura interna, configuraciones de infraestructura ni credenciales.

## Contenido

| Archivo | Se aplica a |
|---|---|
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Reglas de contribución, enlazadas en cada repositorio |
| [`SECURITY.md`](SECURITY.md) | Cómo reportar un problema de seguridad |
| [`.github/pull_request_template.md`](.github/pull_request_template.md) | Plantilla de cada Pull Request |
| [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/) | Formularios de issues: tarea, bug y propuesta de ADR |
| [`.github/workflows/python-quality.yml`](.github/workflows/python-quality.yml) | CI reutilizable para todos los servicios Python |

## Uso del CI reutilizable

Cada servicio crea `.github/workflows/ci.yml` con este contenido:

```yaml
name: CI

on:
  pull_request:
  push:
    branches: [main]

permissions:
  contents: read

jobs:
  quality:
    uses: P-A-C-I-O-L-I/.github/.github/workflows/python-quality.yml@main
```

Parámetros opcionales (`with:`):

| Parámetro | Por defecto | Uso |
|---|---|---|
| `python-version` | `3.14` | Versión de Python |
| `source-dir` | `src` | Carpeta revisada por mypy |
| `check-domain-coverage` | `true` | Exigir el umbral reforzado en la lógica de dominio |
| `domain-coverage-path` | `src/*/domain/*` | Archivos que se consideran lógica de dominio |
| `domain-coverage-min` | `85` | Cobertura mínima de la lógica de dominio |

El umbral global (75%) se define en el `pyproject.toml` de cada servicio, en `[tool.coverage.report] fail_under`.

## Controles del CI

| Job | Qué valida |
|---|---|
| `lint` | Formato y reglas de Ruff |
| `typecheck` | mypy en modo strict |
| `test` | pytest, cobertura global y cobertura de dominio |
| `secrets` | gitleaks sobre todo el historial |
| `dependencies` | pip-audit sobre las dependencias bloqueadas |

Todas las acciones de terceros están fijadas a una versión exacta. Dependabot propone sus actualizaciones mediante Pull Requests.
