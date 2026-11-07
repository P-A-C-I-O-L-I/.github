# Política de seguridad

## Cómo reportar un problema

**Nunca reportes un problema de seguridad en un issue, un Pull Request ni un comentario**, aunque el repositorio sea privado: quedan registrados y visibles para todos sus miembros.

Repórtalo directamente a los responsables de la organización, por un canal privado, a: `[correo de seguridad de P A C I O L I]`.

Incluye qué encontraste, dónde, cómo reproducirlo y desde cuándo crees que existe. No incluyas el secreto ni el dato expuesto en el reporte: basta con indicar dónde está.

## Qué se considera un problema de seguridad

- Una credencial, clave o token en el código o en el historial de Git.
- Un dato real de un cliente o de un tercero en un repositorio.
- Cualquier forma de acceder a datos de otro tenant.
- Una vulnerabilidad en el código o en una dependencia.
- Un acceso indebido a un repositorio, a la organización o a la infraestructura.

## Qué hacer de inmediato

| Situación | Acción inmediata |
|---|---|
| Expusiste una credencial | Rótala o revócala **antes** de cualquier otra cosa, aunque el commit no haya salido de tu máquina |
| Un dato real llegó a un commit | Detén el trabajo, no hagas push y avisa a los responsables |
| Encontraste una vulnerabilidad | No la explotes más allá de lo necesario para confirmarla y repórtala |

## Tiempos de respuesta objetivo

| Severidad | Primera respuesta | Mitigación |
|---|---|---|
| Crítica: datos expuestos, acceso entre tenants o credencial activa | Mismo día | 24 horas |
| Alta | 2 días hábiles | 7 días |
| Media o baja | 5 días hábiles | Siguiente planificación |
