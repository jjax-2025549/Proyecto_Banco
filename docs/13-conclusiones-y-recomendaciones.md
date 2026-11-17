# Conclusiones y recomendaciones

## Conclusiones
1. Se integró un frontend Angular, una API REST en Node.js con TypeScript y una base MySQL en un sistema bancario académico funcional.
2. Las reglas de negocio se aplican en el backend, que es la fuente de verdad, y la interfaz las refleja con mensajes claros.
3. Las transacciones SQL con bloqueo de filas mantienen los saldos consistentes aunque haya operaciones al mismo tiempo.
4. Las 10 pruebas obligatorias y 5 adicionales se automatizaron (15/15 aprobadas) y también están en una colección de Postman. Las 13 pruebas de interfaz quedaron aprobadas con capturas como evidencia.
5. El control de acceso por rol (ADMIN y CAJERO) se valida en el servidor y la interfaz oculta lo que no corresponde.
6. El selector de apariencia (claro, oscuro, automático por hora y color de acento) mejora la comodidad de uso sin afectar la lógica del sistema.
7. Trabajar con un tablero Kanban y commits diarios facilitó llevar el avance de los 10 días.

## Recomendaciones
- Invalidar los tokens al cerrar sesión (lista de revocados o tokens de vida corta con refresh), por la limitación H01.
- Añadir pruebas automáticas del frontend y paginación en los listados.
- Usar migraciones de base de datos en lugar de scripts sueltos.
- Configurar `JWT_SECRET` y credenciales de base de datos únicas por entorno y no dejar valores por defecto.
- Limitar el origen permitido en CORS cuando se despliegue.
