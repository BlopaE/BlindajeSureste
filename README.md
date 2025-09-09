# Blindaje Sureste — Supervisión 4x4

## Confidencialidad
Este proyecto está protegido por un contrato de confidencialidad. Por ese motivo no se publica el código fuente del sistema aquí. En su lugar se documenta la arquitectura, los módulos, los retos técnicos y los resultados alcanzados. 

## Resumen
Proyecto para la programación, ejecución y evaluación de supervisiones de funciones críticas en la División de Distribución Sureste de la CFE. Consta de tres componentes principales: aplicación web, aplicación móvil y una API que conecta ambos con la base de datos. El objetivo principal fue reemplazar procesos manuales (Excel) por un flujo con trazabilidad, evidencias y reportes que facilite la toma de decisiones. 

## Impacto y resultados
- Implementación efectiva: en 5 semanas se realizaron más de 500 supervisiones, lo que demuestra aceptación y efectividad del sistema. 
- Reducción de carga manual y mayor trazabilidad de evidencias fotográficas. 
- Facilitó la generación de métricas e indicadores para la gestión divisional, lo que mejoró la toma de decisiones. 

## Arquitectura general
- Cliente web (ASP.NET 4.5) — interfaz administrativa y de evaluación. 
- Cliente móvil (Android / Java) — ejecución de supervisiones, captura de evidencias y operación offline. 
- API REST (ADO.NET) — operaciones CRUD y puente seguro entre clientes y base de datos. 
- Base de datos relacional (SQL Server 2019) y reporting con SSRS. 

## Diagrama:

## Aplicación Web (ASP.NET 4.5)
- Objetivo: administración, programación y evaluación de supervisiones. 

### Módulos principales
- Autenticación (integración con Directorio Activo + BD). 
- Programación de supervisiones semanales (configurable por zona/proceso/función). 
- Evaluación de supervisiones (visualización de evidencias, fortalezas y debilidades). 
- Gestión de funciones críticas e indicadores. 
- Visualización de reportes incrustados (SSRS). 
- Gestión de usuarios y roles (control de acceso por permisos). 

## Aplicación Móvil (Android / Java)
Objetivo: permitir a supervisores ejecutar supervisiones en campo, capturar evidencias y sincronizar resultados. 

### Características clave
- Autenticación con Directorio Activo (requiere conexión a la intranet o VPN). 
- Modo offline: guardar borradores locales y sincronizar cuando haya conexión. 
- Captura de evidencias fotográficas (con geolocalización y timestamp) y compresión previa al envío. 
- Creación de supervisiones emergentes desde la app (cuando sea necesario). 

## Web API (ADO.NET)
Objetivo: exponer endpoints REST para comunicación entre app móvil y la base de datos, manteniendo integridad y seguridad. 

### Funcionalidades
- Endpoints CRUD para supervisiones, evidencias, usuarios, funciones críticas y reportes. 
- Manejo de errores y validaciones en servidor.

## Base de datos y reportes
- SQL Server 2019 como almacenamiento central. 
- SQLite usado en dispositivos móviles para persistencia local. 
- Reportes con SQL Server Reporting Services (SSRS), integrados en la web por iframes/modals. 

## Seguridad y despliegue
- Operación pensada para la red interna de la División (acceso mediante VPN o certificados, según políticas). 
- Autenticación con Directorio Activo y controles de acceso por roles implementados en la aplicación web. 
- Bitácoras de acceso y auditoría en BD para garantizar trazabilidad. 

## Metodología y control de calidad
- Desarrollo bajo prácticas de XP (iteraciones, historias de usuario, pruebas de aceptación). 
- Integración continua y control de versiones con Azure DevOps / Git. 
- Pruebas de aceptación documentadas (ej. apertura de reportes validada el 14 de junio de 2025). 
