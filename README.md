# Promaty

Sistema de gestión de solicitudes para el ciclo de vida del colaborador, desarrollado como Proyecto
de Título (CAPSTONE) para una empresa del rubro construcción.

## Descripción

Promaty centraliza las solicitudes asociadas al ciclo de vida del colaborador (contratación, anexos,
finiquito, traspasos entre centros de costo, permisos y vacaciones), junto con la gestión de
asistencia y remuneraciones. Está dirigido a jefaturas de obra (que generan las solicitudes) y a
Recursos Humanos (que las gestiona en el ERP oficial de la empresa).

Hoy, este tipo de gestiones se coordina de manera informal (WhatsApp, correo, llamadas), sin registro
ni trazabilidad, y el cálculo de remuneraciones exige mantener alineados un sistema propio y un ERP
externo (Rex+), generando doble digitación y errores. Promaty resuelve esto con un flujo de
aprobación en dos niveles (jefatura de centro de costo → RRHH), control de acceso basado en roles, y
sincronización automatizada (simulada en este proyecto) con Rex+.

> Proyecto autorizado para desarrollo individual por el docente Marco Valenzuela, dado que se basa en
> un proyecto real con cliente real (consultora de TI) donde trabajo actualmente. El sistema
> real se usa solo como referencia de patrones de diseño ya validados — sin datos ni documentos del
> cliente, por contrato de confidencialidad.

## Estructura de este repositorio

Este repositorio contiene las **evidencias académicas de Fase 1** del proceso CAPSTONE. El código
fuente del sistema vive actualmente en repositorios separados (ver [Repositorios del proyecto](#repositorios-del-proyecto)).

```
Fase 1/
├── Evidencias individuales/   → autoevaluaciones y reflexiones individuales
└── Evidencias grupales/       → presentación, formativas y guía de definición del proyecto
```

## Repositorios del proyecto

| Repositorio | Contenido |
|---|---|
| [promaty-backend](https://github.com/KarlaRamirez00/promaty-backend) | Microservicios (Java + Spring Boot) |
| [promaty-frontend](https://github.com/KarlaRamirez00/promaty-frontend) | Frontend (Vue 3 + TypeScript) |

## Tecnologías utilizadas

**Frontend**: Vue 3, TypeScript, Vite, Vuetify

**Backend**: Java, Spring Boot, Spring Cloud (Eureka, OpenFeign) — arquitectura de microservicios:
`eureka-server`, `gateway-server`, `authorizer-server`, `user-server`, `rrhh-server`

**Datos e infraestructura**: PostgreSQL, Git/GitHub, SonarQube (calidad y seguridad)

## Instrucciones para ejecutar el proyecto localmente

Cada servicio se levanta desde su propio repositorio. Ver las instrucciones de instalación y
ejecución en el README de cada uno:

- [promaty-backend](https://github.com/KarlaRamirez00/promaty-backend#readme)
- [promaty-frontend](https://github.com/KarlaRamirez00/promaty-frontend#readme)

## Integrante

| Nombre | Rol |
|---|---|
| Karla Ramírez Hidalgo | Desarrollo full stack, análisis y gestión del proyecto (trabajo individual) |

## Metodología de trabajo

**Kanban**: backlog priorizado con jerarquía Épica → Historia de Usuario → Tarea, tablero con estados
(Por Hacer / En desarrollo / Terminado) y flujo continuo de trabajo, sin sprints de duración fija.
Los checkpoints semanales se documentan como "sprint" (identificador de período) para efectos de
trazabilidad, sin ceremonias formales de Scrum, dado que el proyecto se desarrolla en solitario.

## Arquitectura de la solución

Arquitectura de microservicios: `eureka-server` (service discovery), `gateway-server` (punto de
entrada único), `authorizer-server` (autenticación/JWT), `user-server` (usuarios, roles y permisos) y
`rrhh-server` (dominio de negocio de RRHH), cada uno con su propia base de datos. El frontend
(Vue 3) consume los servicios a través del gateway.
