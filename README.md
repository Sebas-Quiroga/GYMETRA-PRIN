# 🏋️‍♂️ Membresías del GYM  
**Documento Técnico (v2) – Proyecto Académico**

---

## 📖 Descripción del Proyecto  
El sistema **Membresías del GYM** es una solución distribuida para la administración integral de gimnasios. Permite gestionar usuarios, planes de membresía, pagos, control de accesos mediante **códigos QR**, reportes administrativos y notificaciones a clientes.  

La solución se basa en una **arquitectura de microservicios** desplegada en contenedores, garantizando escalabilidad, disponibilidad y seguridad. Incluye:  
- **Aplicación web** para administradores.  
- **Aplicación móvil híbrida** para clientes.  
- Backend en **Spring Boot** con persistencia en **PostgreSQL**.  
- Gestión del ciclo de vida del proyecto con **Scrum** (JIRA, GitHub, Confluence).  

---

## 🎯 Objetivos  

### Objetivo General  
Diseñar e implementar un **sistema distribuido de gestión de membresías** que integre autenticación, membresías, pagos, control de acceso y reportes, asegurando alta disponibilidad y escalabilidad.  

### Objetivos Específicos  
- Implementar **autenticación y autorización** (roles Admin/Cliente) con **JWT/OAuth2**.  
- Desarrollar el módulo de **membresías** (alta, renovación, suspensión, vencimiento).  
- Construir el módulo de **pagos** (integración progresiva con pasarelas externas).  
- Diseñar el **control de acceso QR** y validación en tiempo real.  
- Proveer **reportes financieros y de asistencia** casi en tiempo real.  
- Implementar **microservicios distribuidos** con comunicación síncrona y asíncrona.  
- Gestionar requerimientos en **JIRA/Confluence** y versionado en **GitHub**.  

---

## 📋 Requerimientos y Gestión  
- **Funcionales:** membresías, pagos, control de accesos, reportes.  
- **No funcionales:** seguridad, disponibilidad, escalabilidad, rendimiento.  
- **Herramientas:** JIRA (backlog), Confluence (documentación), GitHub (código).  
- **Artefactos:** Mockups UI (Figma/Balsamiq), UML (casos de uso, clases, secuencia, despliegue), BPMN para flujos críticos.  

---

## ⚙️ Detalles Técnicos  

### Frontend  
- **Frameworks:** Vue.js (web admin), Ionic + Vue (app móvil).  
- **UI:** Vuetify / TailwindCSS.  
- **Estado y comunicación:** Vue Router, Pinia, Axios.  
- **Autenticación:** JWT con interceptores y refresh tokens.  
- **Testing:** Vitest/Jest (unitarias), Playwright (e2e).  

### Backend  
- **Framework:** Java + Spring Boot.  
- **Arquitectura:** Microservicios (Auth, Usuarios, Membresías, Pagos, Acceso, Reportes).  
- **Comunicación:** REST + RabbitMQ/Kafka.  
- **Seguridad:** OAuth2, JWT, CORS, rate limiting.  
- **Descubrimiento/Config:** Spring Cloud, Eureka/Consul.  
- **Testing:** JUnit5, Testcontainers, WireMock.  

### Base de Datos  
- **Relacional:** PostgreSQL (usuarios, membresías, pagos).  
- **NoSQL (opcional):** MongoDB/Cassandra (logs y analítica).  
- **Migraciones:** Liquibase/Flyway.  

### Infraestructura  
- **Contenedores:** Docker.  
- **Orquestación:** Kubernetes (HPA, probes).  
- **CI/CD:** GitHub Actions.  
- **Nube:** AWS / GCP.  
- **Observabilidad:** Prometheus + Grafana, ELK/EFK, OpenTelemetry.  

---

## 🏗️ Arquitectura Distribuida  

### Microservicios principales  
- **Auth & Users:** registro/login, emisión de JWT.  
- **Memberships:** gestión de planes, renovaciones, estados.  
- **Payments:** integración con pasarelas y conciliación.  
- **Access Control:** validación QR y registro de accesos.  
- **Reports:** reportes financieros y de asistencia.  
- **API Gateway:** enrutamiento, seguridad, rate limiting.  
- **Message Broker:** RabbitMQ/Kafka.  

### Flujos clave  
- **Pago:** Orden → Pasarela → Webhook → Evento → Actualización de membresía.  
- **Acceso QR:** Cliente escanea QR → Validación → Registro de evento.  
- **Reportes:** SQL (ingresos) + NoSQL (asistencia).  

---

## 👥 Historias de Usuario  

### Cliente  
- Registro y compra de planes online.  
- Ingreso con QR.  
- Pago con múltiples métodos.  
- Consulta de asistencias y vencimientos.  

### Administrador  
- Gestión de membresías.  
- Reportes de ingresos y asistencias en tiempo real.  

### Técnicas (Sistema)  
- Replicación de autenticación para alta disponibilidad.  
- Escalabilidad de pagos independiente.  
- Balanceo de carga automático.  

---

## 📌 Épicas y Roadmap (JIRA)  

### Épica 1 – Levantamiento y Definición  
- Documentación de requerimientos (JIRA).  
- Configuración repositorio GitHub.  
- Mockups UI y diagramas UML.  
- Modelo ER en PostgreSQL.  
- Presentación inicial.  

### Épica 2 – Configuración y Seguridad  
- Entorno local (Spring Boot + Vue + PostgreSQL).  
- Registro/Login con JWT.  
- Definición de roles.  
- Integración frontend-backend.  

### Épica 3 – Membresías y Acceso QR  
- CRUD planes.  
- Renovación de membresías.  
- Validación QR y registro de accesos.  
- Suspensión/cancelación de membresías.  

### Épica 4 – Pagos  
- CRUD pagos.  
- Simulación con pasarelas (Stripe/PayU).  
- Asociación pago-membresía.  

### Épica 5 – Reportes  
- Reporte de ingresos.  
- Reporte de membresías activas.  
- Registro de accesos QR.  

### Épica 6 – Infraestructura  
- Dockerización de microservicios.  
- Orquestación en Kubernetes.  
- CI/CD con GitHub Actions.  

### Cronograma (Septiembre – Noviembre 2025)  
- **01/09 – 12/09:** Épica 1.  
- **13/09 – 24/09:** Épica 2.  
- **25/09 – 04/10:** Épica 3.  
- **05/10 – 19/10:** Épica 4.  
- **20/10 – 24/10:** Épica 5.  
- **25/10 – 10/11:** Épica 6.  
- **11/11 – 12/11:** Testing final y entrega.  

---

## 🗄️ Modelo de Datos  

| Entidad            | Descripción                                | Atributos clave |
|--------------------|--------------------------------------------|-----------------|
| **Usuario**        | Clientes y administradores                 | id_usuario, nombre, email, contraseña, fecha_registro |
| **Rol**            | Roles del sistema                          | id_rol, nombre_rol |
| **Usuario_Rol**    | Relación Usuario ↔ Rol                     | id_ur, id_usuario, id_rol |
| **Membresía**      | Planes disponibles                         | id_membresía, nombre_plan, precio, duración, estado |
| **Usuario_Membresía** | Relación usuario ↔ membresía adquirida | id_um, id_usuario, id_membresía, fecha_inicio, fecha_fin, estado |
| **Pago**           | Registro de pagos                          | id_pago, id_usuario, id_membresía, monto, fecha_pago, método_pago, estado |
| **Acceso**         | Ingresos mediante QR                       | id_acceso, id_usuario, id_sede, fecha_hora, validado |
| **Sede**           | Información de las sedes del gimnasio      | id_sede, nombre, dirección, ciudad, capacidad_max |

---

## ✅ Conclusiones  
1. **Gestión estructurada:** JIRA asegura trazabilidad y control de cambios.  
2. **Planificación incremental:** roadmap dividido en cortes con entregas funcionales.  
3. **Solidez tecnológica:** stack moderno (Spring Boot, Vue.js, PostgreSQL, Docker, Kubernetes).  
4. **Práctica profesional:** aplicación de metodologías ágiles y despliegues reales.  
5. **Valor incremental:** MVP → Membresías/Accesos → Reportes/Infraestructura.  
6. **Adaptabilidad:** mejora continua de requerimientos y arquitectura.  

---

## 👨‍💻 Autores  
- Jhon Jamez Nieto Perez  
- Johan Sebastian Naranjo Quiroga  
- Juan Felipe Narvaez Amaya  

**Dirigido al docente:**  
Jesus Ariel Gonzalez Bonilla  

📍 Corporación Universitaria del Huila – Ingeniería de Sistemas Distribuidos  
📅 Semestre 8 – Neiva, Agosto 2025  
