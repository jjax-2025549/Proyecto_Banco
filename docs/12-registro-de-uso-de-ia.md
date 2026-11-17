# Registro de uso de inteligencia artificial

La IA se usó como herramienta de apoyo, como permite la sección 12 de la guía. Abajo queda el registro de cada uso con lo que apliqué, lo que cambié y cómo entiendo la solución.


| Herramienta | Prompt | Resultado | Aplicación | Modificación | Comprensión |
|---|---|---|---|---|---|
| Claude (Anthropic) | Consulté cómo implementar un selector de tema claro y oscuro en un proyecto desarrollado con Angular y TypeScript, conectado a una base de datos MySQL, y qué debía considerar para aplicarlo correctamente | Explicación sobre el uso de variables CSS, clases para los temas y manejo del estado del tema desde Angular | Utilicé las indicaciones como referencia para implementar el selector de tema en la interfaz del sistema bancario | Adapté los estilos a los colores y componentes de mi proyecto, ajustando los elementos que cambiaban según el tema seleccionado | Comprendí cómo funcionan los estilos de cada tema, cómo Angular permite cambiar clases dinámicamente y cómo mantener la apariencia seleccionada |
| Claude (Anthropic) | Pregunté cómo organizar los servicios y componentes de Angular para mantener una comunicación adecuada con una API desarrollada en Node.js y TypeScript, conectada a MySQL | Orientación sobre la separación de responsabilidades entre componentes, servicios, rutas y controladores | Apliqué las recomendaciones para comprender mejor la organización del frontend y su comunicación con el backend | Revisé la estructura existente y adapté algunos elementos según las necesidades del sistema | Comprendí cómo se comunican las diferentes capas del proyecto y por qué es importante separar la interfaz, la lógica y las operaciones de la base de datos |
| Claude (Anthropic) | Consulté cómo identificar posibles errores en plantillas HTML de Angular y cómo comprobar que las funciones, variables, servicios y componentes estuvieran correctamente relacionados con TypeScript | Explicación sobre directivas, eventos, interpolaciones, imports y comunicación entre archivos HTML y TypeScript | Utilicé las explicaciones para revisar diferentes componentes de la interfaz y detectar posibles problemas | Revisé los archivos señalados y realicé los ajustes necesarios según la estructura de mi proyecto | Comprendí cómo se relacionan las plantillas HTML con los archivos TypeScript y cómo identificar errores comunes sin modificar innecesariamente el código |



## Puntos que debo poder explicar en la defensa

1. Cómo funcionan los depósitos, retiros y transferencias, y por qué se debe asegurar que las operaciones se completen correctamente.
2. Cómo funciona el inicio de sesión con JWT y cómo el sistema verifica que el usuario tenga permiso para acceder.
3. Cómo funciona el cambio de tema claro y oscuro, incluyendo el modo automático según la hora del día.
4. Cómo se relacionan las tablas `cuenta`, `movimiento` y `transferencia` dentro de la base de datos.
5. Cómo se realizaron las pruebas para comprobar que las funciones principales del sistema trabajen correctamente (P001–P015 y U01–U13).
6. Cómo funciona el cierre de sesión y qué sucede con el token cuando el usuario sale del sistema (hallazgo H01).
