# Registro de errores y correcciones

| ID | Descripción del error | Causa | Corrección | Estado |
|---|---|---|---|---|
| E01 | Al generar el frontend, Angular CLI mostró que requería una versión de Node más nueva que la instalada | La versión más reciente del CLI exige Node muy reciente | Se fijó Angular 20 (compatible con Node 20.19+ y 22) | Corregido |
| E02 | `TS2349: This expression is not callable` al guardar clientes | Se asignaba a una variable un `Observable` de dos tipos distintos (crear/actualizar) | Se tipó la variable como `Observable<Resp<unknown>>` | Corregido |
| E03 | La API respondía `500 Error interno` en todas las rutas | MySQL no estaba en ejecución (`ECONNREFUSED 127.0.0.1:3306`) | Iniciar el servicio MySQL y ejecutar `pnpm db:init`; se agregó esta guía al README | Corregido |
| E04 | `TS2322: Type 'string' is not assignable to type 'boolean'` al usar la directiva de conteo animado en el resumen | El atributo `dinero` sin enlace llega como texto y la entrada se declaró como booleano | Se enlazó explícitamente: `[dinero]="true"` | Corregido |
| E05 | `TS2393: Duplicate function implementation` en el login | Se agregó un método `usar()` que ya existía para autocompletar credenciales | Se conservó una sola implementación | Corregido |

| E06 | En la primera corrida de las pruebas de interfaz, U04 salió como fallida | El script de prueba eligió como cuenta destino la cuenta `100-0000003`, que es inactiva; el sistema la rechazó con HTTP 409 | No era un fallo del sistema sino de la prueba: se cambió el destino a una cuenta activa y se dejó la transferencia a cuenta inactiva como prueba aparte (U13) | Corregido |
| E07 | Aparecen errores `ERR_NAME_NOT_RESOLVED` en la consola del navegador durante las pruebas | El entorno de pruebas no tenía salida a Internet y no pudo descargar la fuente IBM Plex Sans de Google Fonts | La interfaz usa la fuente de respaldo y funciona igual; con conexión la fuente carga normalmente | Sin impacto |
| H01 | Después de pulsar cerrar sesión, `GET /api/auth/me` sigue respondiendo 200 con el mismo token | El JWT es sin estado: el servidor no guarda una lista de tokens revocados. El frontend descarta el token, pero este sigue válido hasta expirar (8 h) | Se documenta como limitación conocida. Mejora propuesta: tokens de vida corta con refresh o lista de tokens revocados | Documentado |
