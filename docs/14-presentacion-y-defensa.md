# Presentación y defensa

Duración: 12 a 15 minutos, siguiendo la sección 15 de la guía. Trabajo individual: presento todas las partes.

## Guion por bloques
| Minutos | Bloque | Qué digo y muestro |
|---|---|---|
| 2 | Problema y objetivos | Registrar clientes y mover dinero a mano genera errores de saldo y no deja trazabilidad. Objetivo: un sistema con frontend, API y base de datos que aplique las reglas de negocio y registre cada operación (`docs/01`). |
| 2 | Arquitectura y base de datos | Tres capas: Angular, Express + TypeScript y MySQL (`docs/04`). Muestro el diagrama ER y explico las tablas `cliente`, `usuario`, `cuenta`, `tipo_cuenta`, `movimiento` y `transferencia` (`docs/06` y `docs/07`). |
| 5 | Demostración | Ver guion de abajo. |
| 2 | Pruebas y errores corregidos | 15/15 en la API, 13/13 en la interfaz y la colección de Postman (`docs/09`). Cuento los errores del registro (`docs/10`), por ejemplo E06 y el hallazgo H01. |
| 1–2 | Mantenimiento, IA y conclusiones | Despliegue en Render, ramas `ft-jjax-2025549` → `develop` → `main`, uso de IA documentado (`docs/12`) y recomendaciones (`docs/13`). |

## Guion de la demostración (5 minutos)
1. Entrar como `admin` / `Admin123` y mostrar el resumen.
2. Cambiar la apariencia: oscuro, claro y automático (explicar el rango 19:00–06:00).
3. Registrar un cliente con datos ficticios y crear su cuenta con saldo inicial.
4. Hacer un depósito y un retiro. Intentar un retiro mayor al saldo y mostrar el rechazo.
5. Transferir entre dos cuentas y revisar ambos saldos. Intentar transferir a la misma cuenta y a una cuenta inactiva.
6. Abrir Movimientos, filtrar por cuenta y tipo, y exportar el CSV.
7. Cerrar sesión, entrar como `cajero1` / `Cajero123` y mostrar que no aparece el botón de desactivar.

## Preguntas que me pueden hacer
| Pregunta | Respuesta corta |
|---|---|
| ¿Por qué usan transacciones? | Para que un depósito, retiro o transferencia se guarde completo o no se guarde. Si falla algo, se hace `ROLLBACK`. |
| ¿Qué hace `FOR UPDATE`? | Bloquea la fila de la cuenta hasta terminar la transacción, así dos operaciones simultáneas no pisan el saldo. |
| ¿Cómo evitan interbloqueos en una transferencia? | Bloqueo las dos cuentas siempre en orden ascendente por id. |
| ¿Cómo funciona el JWT? | Al iniciar sesión el servidor firma un token con id, usuario y rol. El interceptor del frontend lo manda en `Authorization: Bearer`. |
| ¿Dónde se valida el rol? | En el backend con `soloRol('ADMIN')`; el frontend solo oculta los botones. |
| ¿Cómo cambia el tema automático? | `ThemeService` revisa la hora local cada 30 s y aplica oscuro dentro del rango configurado; guarda la preferencia en `localStorage`. |
| ¿Por qué guardan `saldo_resultante` en `movimiento`? | Para que el historial muestre el saldo después de cada operación sin recalcular. |
| ¿Qué limitación tiene el cierre de sesión? | El JWT sigue válido hasta expirar porque el servidor no lo revoca (H01). |

## Posibles modificaciones puntuales
- Cambiar el rango por defecto del modo automático: `darkFrom` y `darkTo` en `frontend/src/app/core/theme.service.ts`.
- Cambiar el monto máximo permitido: `backend/src/utils/validar.ts`.
- Agregar un campo a `cliente`: tabla en `database/01_estructura.sql`, validación en el controlador y formulario en `pages/clientes.html`.
