# Mesa de Servicios TI - TecnoColombia S.A.S. (GLPI)
**Curso:** Gestión de TI (202016904) - Fase 4  
**Institución:** Universidad Nacional Abierta y a Distancia (UNAD)  
**Semestre / Periodo:** 2026  

---

## 1. Descripción del Proyecto
Este proyecto contiene la implementación, configuración y operación de una **Mesa de Servicios TI en GLPI (ITIL Service Desk)** para la empresa ficticia **TecnoColombia S.A.S.** El despliegue está orquestado mediante contenedores Docker, integrando una base de datos relacional MariaDB, el core de GLPI y un servidor local de captura de correos electrónicos (Mailpit).

La solución cubre la gestión de incidentes, solicitudes de servicio, gestión de problemas, acuerdos de nivel de servicio (SLA), reglas automáticas de asignación y encuestas de satisfacción de usuarios.

---

## 2. Requisitos Previos
* **Docker Desktop** (macOS Intel/Apple Silicon, Linux o Windows) instalado y en ejecución.
* **Docker Compose v2+**.
* Puertos locales disponibles:
  * `8081` (Mesa de Servicios GLPI - modificable en `.env`)
  * `8025` (Buzón de pruebas Mailpit)

---

## 3. Despliegue de la Plataforma

1. **Clonar el repositorio:**
   ```bash
   git clone <URL_DEL_REPOSITORIO>
   cd glpi-mesa-servicios
   ```

2. **Configurar variables de entorno:**
   Copie el archivo de ejemplo y defina las contraseñas deseadas:
   ```bash
   cp .env.example .env
   ```
   Edite `.env` con sus parámetros de base de datos y puerto.

3. **Iniciar los contenedores en segundo plano:**
   ```bash
   docker compose up -d
   ```

4. **Verificar estado de los contenedores:**
   ```bash
   docker compose ps
   ```

5. **Acceso a los servicios:**
   * **Mesa de Servicios GLPI:** [http://localhost:8081](http://localhost:8081)
   * **Buzón de Notificaciones (Mailpit):** [http://localhost:8025](http://localhost:8025)

---

## 4. Guía de Configuración Inicial (ITIL en GLPI)

1. **Entidad Organizacional:**
   * Crear la entidad hija `TecnoColombia S.A.S.` bajo la Entidad Raíz y seleccionarla como contexto de operación permanente.
   * Activar la encuesta de satisfacción al 100% con escala de calificación de 1 a 5.

2. **Grupos de Soporte:**
   * *Soporte Nivel 1 (Mesa de servicios)* (Asignable a tickets)
   * *Soporte Nivel 2*
   * *Soporte Nivel 3*
   * *Redes*
   * *Aplicaciones*

3. **Catálogo de Categorías ITIL:**
   * *Aplicación (CRM, Correo corporativo)*
   * *Conectividad*
   * *Equipo (computadores, impresoras, periféricos)*
   * *Usuarios*
   * *Contraseñas e información*

4. **Acuerdos de Nivel de Servicio (SLA):**
   * Configurados con calendario laboral `Lunes a viernes 8:00-18:00`:
     * **Crítica:** TTO 15 min / TTR 4 h
     * **Alta:** TTO 30 min / TTR 8 h
     * **Media:** TTO 2 h / TTR 24 h
     * **Baja:** TTO 4 h / TTR 48 h

5. **Reglas de Negocio Automáticas:**
   * *Error de red a grupo Redes:* Categoría = Conectividad ➔ Asignar a grupo Redes.
   * *Prioridad alta o crítica a Nivel 3:* Prioridad = Alta o Muy alta ➔ Asignar a Soporte Nivel 3.
   * *Asignar SLA por prioridad:* Aplica el SLA respectivo automáticamente.
   * *Tickets nuevos a Nivel 1:* Tickets sin grupo asignado ➔ Asignar a Soporte Nivel 1.

6. **Notificaciones de Correo:**
   * Configuración SMTP: Servidor `mail`, puerto `1025`, remitente `mesa@tecnocolombia.local`, sin autenticación.
   * Notificaciones activadas: Nuevo ticket, Ticket asignado / actualización y Cierre de ticket.

---

## 5. Estructura de Roles del Equipo

| Integrante | Rol en el Proyecto | Usuario en GLPI | Perfil ITIL | Grupo de Soporte |
| :--- | :--- | :--- | :--- | :--- |
| **Jesús** | Soporte Nivel 1 (Mesa de ayuda) | `agente.n1` | Technician | Soporte Nivel 1 (Mesa de servicios) |
| **Saray** | Soporte Nivel 2 (Especialista soporte) | `saray.n2` | Technician | Soporte Nivel 2 |
| **Luis Emir** | Soporte Nivel 3 (Infraestructura / Redes / Apps) | `luis.n3` | Technician | Soporte Nivel 3, Redes, Aplicaciones |
| **Juvan** | Gestor de la Mesa de Servicios | `gestor.mesa` | Supervisor | Gestión / Supervisión |
| **Yenny** | Cliente / Solicitante | `cliente.01` | Self-Service | Área Usuaria / Solicitante |

---

## 6. Documentación Adicional
En la carpeta [`docs/`](./docs/) se encuentran disponibles:
* [`docs/tabla_tickets.md`](./docs/tabla_tickets.md): Relación cronológica de los 10 casos simulados con trazabilidad de tiempos, escalamientos y encuestas.
* [`docs/kpi.md`](./docs/kpi.md): Indicadores clave de rendimiento (TTO, TTR, FCR, cumplimiento de SLA y satisfacción).
