

## Módulos obligatorios (sección 3)
| Módulo | Dónde está | Estado |
|---|---|---|
| Autenticación | `auth.routes.ts`, `auth.controller.ts`, `pages/login` | Cumple |
| Clientes | `clientes.routes.ts`, `pages/clientes` | Cumple |
| Cuentas | `cuentas.routes.ts`, `pages/cuentas` | Cumple |
| Depósitos | `POST /depositos`, `pages/operaciones` | Cumple |
| Retiros | `POST /retiros`, `pages/operaciones` | Cumple |
| Transferencias | `POST /transferencias`, `pages/operaciones` | Cumple |
| Movimientos | `GET /movimientos`, `pages/movimientos` | Cumple |
| Consultas | `pages/consultas` | Cumple |
| Reportes | `GET /reportes/resumen`, `pages/resumen` | Cumple |
| Validaciones | `utils/validar.ts` y reglas en `operaciones.service.ts` | Cumple |

## Reglas de negocio (sección 4)
Las 10 reglas están cubiertas; la tabla de pruebas por regla está en [`09-matriz-de-pruebas.md`](09-matriz-de-pruebas.md).

## Tecnologías (sección 5)
Angular + TypeScript, Node.js + TypeScript con API REST, MySQL, Postman y Git/GitHub. Frontend, backend y base de datos están separados.

## Base de datos y API (secciones 8 y 9)
| Requisito | Estado |
|---|---|
| Entidades Cliente, Usuario, Cuenta, TipoCuenta, Movimiento y Transferencia | Cumple (`database/01_estructura.sql`) |
| ERD, modelo lógico y script SQL con PK y FK | Cumple (`docs/06`, `docs/07`) |
| Clientes: GET, GET por id, POST, PUT/PATCH y desactivación lógica | Cumple |
| Cuentas: GET, GET por id, POST y PUT/PATCH | Cumple |
| Movimientos: GET, GET por cuenta y POST | Cumple |
| Depósitos, retiros, transferencias y login: POST | Cumple |
| Rutas documentadas en el README | Cumple (`docs/08-api-endpoints.md`) |

## Pruebas obligatorias (sección 13)
P001 a P010 aprobadas, más P011 a P015 adicionales (15/15) y U01 a U13 de interfaz (13/13).

## Documentación final (sección 14) y productos finales (sección 16)
| Elemento | Archivo |
|---|---|
| README, instalación y credenciales ficticias | `README.md` |
| Problema, solución y objetivos | `docs/01` |
| Requerimientos e historias de usuario (17) | `docs/02`, `docs/03` |
| Diagramas y arquitectura | `docs/04`, `docs/05` |
| Base de datos y script SQL | `docs/06`, `docs/07`, `database/` |
| Endpoints | `docs/08` |
| Matriz de pruebas y registro de errores | `docs/09`, `docs/10` |
| Manual de usuario | `docs/11` |
| Registro de uso de IA | `docs/12` |
| Conclusiones y recomendaciones | `docs/13` |
| Presentación y defensa | `docs/14` |
| Tablero Kanban | `docs/15` |

## Entrega diaria (sección 11)
Commits frecuentes en `ft-jjax-2025549`, tarjetas con responsable en Trello, capturas y resultados de pruebas en `docs/evidencias/`, y una bitácora por día en `docs/bitacora/`.

## Despliegue
Configurado para Render con `render.yaml` (un solo servicio que sirve el frontend compilado). La base MySQL debe estar en un proveedor externo.
