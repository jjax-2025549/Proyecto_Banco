# Matriz de pruebas

## Pruebas obligatorias (API)
Ejecutadas con `pnpm test:api` (backend) el 14/11/2026. Evidencia completa: [`evidencias/pruebas-api-P001-P010.txt`](evidencias/pruebas-api-P001-P010.txt). También están en la colección de Postman.

| ID | Prueba | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|
| P001 | Login válido | Permite acceso | HTTP 200 con token | Aprobada |
| P002 | Login inválido | Muestra mensaje de error | HTTP 401 "Credenciales inválidas." | Aprobada |
| P003 | Registrar cliente | Cliente almacenado | HTTP 201, cliente con id | Aprobada |
| P004 | Crear cuenta | Cuenta asociada al cliente | Cuenta con `cliente_id` correcto | Aprobada |
| P005 | Depósito válido | Saldo incrementado | 100 → 150 | Aprobada |
| P006 | Retiro con saldo suficiente | Saldo disminuido | 150 → 120 | Aprobada |
| P007 | Retiro superior al saldo | Operación rechazada | HTTP 422 saldo insuficiente | Aprobada |
| P008 | Transferencia válida | Se actualizan ambas cuentas | Origen 100, destino 20 | Aprobada |
| P009 | Transferencia a misma cuenta | Operación rechazada | HTTP 422 | Aprobada |
| P010 | Cuenta inactiva | No permite operaciones | Depósito, retiro y transferencia: HTTP 409 | Aprobada |

### Pruebas adicionales (control de acceso y validaciones)

| ID | Prueba | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|
| P011 | Cajero intenta desactivar un cliente | Acceso denegado | HTTP 403 | Aprobada |
| P012 | Cajero consulta clientes | Permite la consulta | HTTP 200 | Aprobada |
| P013 | Depósito con monto cero | Operación rechazada | HTTP 400 | Aprobada |
| P014 | Registrar cliente con DPI repetido | Operación rechazada | HTTP 409 | Aprobada |
| P015 | Consultar cuentas sin sesión | Acceso denegado | HTTP 401 | Aprobada |

Resultado global: **15/15 pruebas aprobadas**.

## Pruebas de interfaz
Ejecutadas en el navegador (Chromium automatizado con Playwright) contra la aplicación compilada, el 14/11/2026. Cada prueba tiene su captura en `docs/evidencias/`.

| ID | Prueba | Resultado esperado | Resultado obtenido | Evidencia | Estado |
|---|---|---|---|---|---|
| U01 | Iniciar sesión desde la pantalla de login | Entra al resumen | Redirige a `/resumen` | `U01-login.png`, `U01-resumen.png` | Aprobada |
| U02 | Registrar un cliente desde el formulario | Aparece en la tabla | Mariana Castillo aparece en la lista | `U02-clientes-formulario.png`, `U02-clientes-tabla.png` | Aprobada |
| U03 | Crear una cuenta para ese cliente | Aparece con su saldo inicial | Cuenta nueva con Q500.00 | `U03-cuenta-formulario.png`, `U03-cuentas-tabla.png` | Aprobada |
| U04 | Realizar depósito, retiro y transferencia desde Operaciones | Mensajes de éxito y saldos actualizados | Los tres movimientos aparecen en el historial | `U04-deposito.png`, `U04-retiro.png`, `U04-transferencia.png` | Aprobada |
| U05 | Intentar retirar más del saldo | Mensaje de error claro | Aviso de que el monto supera el saldo y el botón queda bloqueado | `U05-retiro-rechazado.png` | Aprobada |
| U06 | Filtrar movimientos por cuenta y tipo | La tabla se filtra | Solo quedan los depósitos de la cuenta elegida | `U06-movimientos-filtrados.png`, `U06-consultas.png` | Aprobada |
| U07 | Cambiar a modo oscuro y a modo claro | Los colores cambian al instante | El fondo pasa de oscuro a claro sin recargar | `U07-resumen-modo-oscuro.png`, `U07-resumen-modo-claro.png` | Aprobada |
| U08 | Activar modo automático y modificar el rango horario | El tema se adapta a la hora actual | Muestra el rango 19:00–06:00 y permite editarlo | `U08-modo-automatico.png` | Aprobada |
| U09 | Cambiar el color de acento y recargar la página | El color se conserva | El acento sigue igual tras recargar | `U09-acento-persistente.png` | Aprobada |
| U10 | Cerrar sesión e intentar abrir `/clientes` | Redirige al login | Vuelve a `/login` | `U10-redireccion-login.png` | Aprobada |
| U11 | Iniciar sesión con contraseña incorrecta | Muestra mensaje de error | "Credenciales inválidas" en pantalla | `U11-login-invalido.png` | Aprobada |
| U12 | Entrar como cajero y abrir Clientes | No ve el botón Desactivar | La tabla solo muestra Editar | `U12-cajero-clientes.png` | Aprobada |
| U13 | Transferir hacia una cuenta inactiva | Operación rechazada | El sistema responde que la cuenta está inactiva | `U13-transferencia-cuenta-inactiva.png` | Aprobada |

Resultado global de interfaz: **13/13 pruebas aprobadas**.

## Cobertura de reglas de negocio
| Regla (guía, sección 4) | Prueba |
|---|---|
| 1. La cuenta pertenece a un cliente | P004 |
| 2. No retirar más del saldo | P007, U05 |
| 3 y 4. Depósitos y retiros mayores que cero | P013 |
| 5. Transferencia con cuentas válidas | P008 |
| 6. Cuenta origen con saldo suficiente | P007 (retiro) y validación en `transferir` |
| 7. Sin transferencias a la misma cuenta | P009 |
| 8. Operación registrada con fecha, tipo, monto y cuentas | P005, P006, P008, U04 |
| 9. Cuenta inactiva no opera | P010, U13 |
| 10. Solo información ficticia | Datos de `database/02_datos_ficticios.sql` |
