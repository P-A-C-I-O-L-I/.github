# Cómo contribuir en P A C I O L I

Resumen obligatorio del proceso. La versión completa, con cada paso justificado, es la guía **ENG-002 · Flujo de trabajo con Git y GitHub** del repositorio `pacioli-architecture`.

## Principios

- `main` siempre funciona. Nadie hace cambios directamente en `main`.
- Todo cambio entra por Pull Request, incluidos los propios, los urgentes y los pequeños.
- Un PR resuelve una sola tarea.
- Las ramas duran días, no semanas.
- Todos los commits están firmados y aparecen como **Verified**.
- Los PRs se integran con **Squash and merge**.

## Nombres de ramas

`tipo/descripcion-corta`, en inglés, minúsculas y con guiones. Ejemplo: `feat/header-fingerprint`.

## Mensajes de commit y títulos de PR

[Conventional Commits](https://www.conventionalcommits.org/): `tipo(alcance): descripción`, en inglés, en imperativo y con un máximo de 72 caracteres.

| Tipo | Uso |
|---|---|
| `feat` | Nueva funcionalidad |
| `fix` | Corrección de un error |
| `docs` | Solo documentación |
| `test` | Solo tests |
| `refactor` | Cambio interno sin alterar el comportamiento |
| `chore` | Mantenimiento y configuración |
| `ci` | Workflows de integración continua |

## Ciclo de un cambio

1. `git switch main && git pull`
2. `git switch -c tipo/descripcion-corta`
3. Trabajar y revisar con `git status` y `git diff`
4. `git add` de los archivos del cambio
5. `git commit -m "tipo(alcance): descripción"`
6. `git push -u origin tipo/descripcion-corta`
7. Abrir el PR con la plantilla completa y `Closes #N` o `Refs #N`
8. Verificar: **Files changed**, commits **Verified**, CI en verde y aprobación
9. **Squash and merge**
10. `git switch main && git pull && git branch -d tipo/descripcion-corta`

## Definition of Done

Un cambio está terminado solo si cumple sus criterios de aceptación, tiene tests en los niveles que corresponden, pasa Ruff, mypy y los umbrales de cobertura, tiene la documentación actualizada, está cubierto por la suite de aislamiento si toca datos de tenants y fue aprobado por otro miembro del equipo.

## Datos y secretos

Ningún dato real ni ninguna credencial entra a un repositorio, aunque sea privado. Ante cualquier duda, se detiene el trabajo y se consulta [SECURITY.md](SECURITY.md).

## Trabajo sin revisor disponible

Cuando solo un miembro del equipo está activo, el autor completa la checklist del PR, lo integra y le agrega la etiqueta `needs-ratification`. El otro miembro revisa todos los PRs con esa etiqueta cuando se incorpora.
