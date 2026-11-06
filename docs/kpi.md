# Métricas y KPIs de la Mesa de Servicios TI - TecnoColombia S.A.S.
**Curso:** Gestión de TI (202016904) - Fase 4  
**Universidad:** Universidad Nacional Abierta y a Distancia (UNAD)  
**Semana Simulada:** 02 de noviembre al 06 de noviembre de 2026  
**Entidad Operativa:** TecnoColombia S.A.S.  

---

## Tabla Oficial de Indicadores Clave de Rendimiento (KPIs)

| Indicador (KPI) | Valor Real Obtenido (GLPI) | Meta / Referencia | Estado / Cumplimiento | Observaciones de Gestión |
| :--- | :---: | :---: | :---: | :--- |
| **Tiempo medio de respuesta (TTO promedio)** | **28,00 minutos** | < 45 minutos | Cumple | Primera atención ágil por parte de Nivel 1 y derivación inmediata. |
| **Tiempo medio de resolución (TTR promedio)** | **5,55 horas** (333 min) | < 8,00 horas | Cumple | Promedio consolidado de los 10 casos en la semana simulada. |
| **Cumplimiento general de SLA (%)** | **90,00 %** | > 85 % | Cumple | 9 de 10 tickets dentro del SLA pactado. Un único caso de análisis fuera de tiempo (T-08). |
| **Resolución en primer contacto (%) (FCR)** | **30,00 %** | > 25 % | Cumple | 3 tickets (T-01, T-02, T-10) solucionados directamente en Nivel 1 sin necesidad de escalamiento. |
| **Tasa de tickets escalados (%)** | **70,00 %** | < 75 % | Controlado | 7 tickets escalados a Nivel 2 o Nivel 3 por su complejidad técnica (40% llegaron a Nivel 3: T-03, T-05, T-07, T-09). |
| **Volumen: Tickets abiertos y en proceso** | **0 tickets (0 %)** | N/A | Normal | Todo el ciclo de la semana operativa culminó satisfactoriamente. |
| **Volumen: Tickets resueltos y cerrados** | **10 tickets (100 %)** | 100 % | Cumple | 100% de los tickets con solución aceptada y estado cerrado. |
| **Satisfacción promedio de usuarios (1 a 5)** | **4,40 / 5,00** (88,0 %) | > 4,00 / 5,00 | Excelente | Calificaciones entre 4 y 5 en el 90% de los casos; calificación de 2 en el ticket T-08 por demora atribuida a terceros. |

---

## Análisis de Casos Especiales

* **Caso de Incumplimiento Intencional de SLA (T-08):**  
  El ticket *T-08 (Conectividad: sin acceso a un servicio específico de facturación)* registró un tiempo de resolución real de **30,5 horas**, superando el SLA asignado de 24 horas. La causa raíz fue la demora en la respuesta del proveedor externo de hosting para la habilitación de reglas en el firewall perimetral (28 horas de espera externa). Este incidente generó una encuesta con calificación de **2/5**, lo que evidencia la necesidad de establecer OLAs (Acuerdos de Nivel Operacional) más estrictos y penalizaciones con proveedores externos.

* **Eficacia del Escalamiento Jerárquico a Nivel 3:**  
  Los 4 incidentes de alta complejidad escalados a Nivel 3 (*T-03: CRM caído*, *T-05: correo corporativo*, *T-07: bucle en red troncal*, *T-09: bloqueo de cuentas y respaldos*) fueron diagnosticados en su causa raíz y solucionados dentro de los márgenes críticos y altos de SLA (resoluciones de 3h, 4h, 5h y 6h respectivamente) por el especialista Luis Emir Guerrero Duran.
