#Membresías del GYM 🏋️‍♂️

Sistema distribuido para la gestión de usuarios, planes de membresía, pagos y control de acceso en gimnasios con múltiples sedes.
El proyecto está diseñado con arquitectura de microservicios, aplicaciones web y móvil, e integración con herramientas modernas de desarrollo, despliegue y gestión.

#📌 Descripción

El sistema permite a clientes registrarse, pagar, renovar membresías y acceder al gimnasio mediante códigos QR.
Los administradores pueden gestionar usuarios, membresías, pagos y obtener reportes en tiempo real.

Se construye bajo un enfoque ágil (Scrum) utilizando JIRA para la gestión de épicas/sprints y GitHub para el control de versiones.

#🎯 Objetivos
General

Diseñar e implementar un sistema distribuido de gestión de membresías que integre autenticación, membresías, pagos, control de acceso y reportes, garantizando alta disponibilidad, seguridad y escalabilidad.

Específicos

Implementar autenticación y autorización con roles (Administrador, Cliente) usando JWT/OAuth2.

Desarrollar el módulo de membresías (alta, renovación, suspensión, vencimiento).

Construir el módulo de pagos con pasarelas externas.

Diseñar el control de acceso basado en código QR y validación en tiempo real.

Generar reportes de ingresos y asistencias.

Definir arquitectura distribuida con microservicios y mensajería asíncrona.

Evaluar persistencia SQL y NoSQL (polyglot persistence).

#🛠️ Tecnologías
   #Frontend

Vue.js (web admin)

Ionic + Vue (app móvil)

Tailwind / Vuetify, Axios, Vue Router, Pinia

Pruebas: Vitest/Jest, Playwright

#Backend

Java + Spring Boot (microservicios: Autenticación, Usuarios, Membresías, Pagos, Acceso, Reportes)

Comunicación vía REST + RabbitMQ/Kafka

Seguridad: OAuth2 + JWT

Documentación de APIs con Swagger/OpenAPI

Base de Datos

PostgreSQL / MySQL (usuarios, membresías, pagos)

MongoDB / Cassandra (logs y analítica en tiempo real)

Migraciones con Liquibase/Flyway

Infraestructura

Contenedores con Docker

Orquestación con Kubernetes

GitHub Actions para CI/CD

Observabilidad: Prometheus + Grafana, ELK/EFK, OpenTelemetry

#🏗️ Arquitectura
Microservicios principales

Auth & Users Service → Login, roles, JWT

Memberships Service → Gestión de planes y renovaciones

Payments Service → Pagos y conciliación con pasarelas

Access Control Service → Validación QR y registro de accesos

Reports Service → Reportes de ingresos y asistencias

API Gateway → Autenticación, enrutamiento y rate limiting

Service Registry & Config → Descubrimiento y configuración centralizada

#📲 Historias de Usuario (ejemplos)

Cliente: registrarse, pagar membresía, ingresar con QR, consultar asistencias.

Administrador: gestionar membresías, ver ingresos, consultar estadísticas de asistencia.

Sistema: replicación de servicios críticos, balanceo de carga, almacenamiento distribuido.

#📅 Roadmap Académico
~#Corte 1 – Fundamentos (Semanas 1-4)

Requerimientos, mockups, diagramas

Login y gestión básica de usuarios

Corte 2 – Core del negocio (Semanas 5-8)

Gestión de membresías

Control de acceso básico

Corte 3 – Optimización y despliegue (Semanas 9-12)

Pagos y reportes

Dockerización y Kubernetes

CI/CD con GitHub Actions

👥 Autores

Jhon Jamez Nieto Perez

Johan Sebastian Naranjo Quiroga

Juan Felipe Narvaez Amaya

Dirigido por: Jesús Ariel González Bonilla
Corporación Universitaria del Huila – Ingeniería de Sistemas
jira url https://gymetra.atlassian.net/jira/software/projects/SCRUM/boards/1/backlog?epics=visible&issueParent=10001%2C10014%2C-7320340678%2C10024&atlOrigin=eyJpIjoiNWMyYWZhMDQ3MDA3NGQ5YzkwMWE1MDYyOWRmMmIwZDMiLCJwIjoiaiJ9
