# Módulo 4: Pila de Observabilidad y Monitoreo con Docker, Prometheus y Grafana (`lab-monitoring-stack`)

Este laboratorio implementa una pila de monitoreo completa utilizando la arquitectura estándar de observabilidad en contenedores: **Prometheus** como base de datos de series temporales, **cAdvisor** como recolector de métricas a nivel de contenedor/sistema, y **Grafana** como plataforma de visualización en tiempo real.

---

## 📐 Arquitectura del Sistema
```text
  ┌─────────────────┐       Scrape (5s)      ┌─────────────────┐
  │    cAdvisor     │ ─────────────────────> │   Prometheus    │
  │  (Puerto 8081)  │                        │  (Puerto 9090)  │
  └─────────────────┘                        └────────┬────────┘
                                                      │
                                                      │ Consulta / PromQL
                                                      │
                                                 ┌────────▼────────┐
                                                 │     Grafana     │
                                                 │  (Puerto 3000)  │
                                                 └─────────────────┘

Tecnologías Utilizadas :

Docker & Docker Compose: Orquestación de la pila de observabilidad.

cAdvisor (gcr.io/cadvisor/cadvisor:v0.47.0): Métricas de uso de CPU, RAM, Red y Disco de los contenedores.

Prometheus (prom/prometheus:latest): Recolección y almacenamiento de métricas mediante scraping.

Grafana (grafana/grafana:latest): Tableros visuales y consultas PromQL.
