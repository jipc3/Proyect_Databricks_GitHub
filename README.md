<div align="center">

# 🏢 ETL Ranking de Empresas del Ecuador
### Arquitectura Medallion en Azure Databricks

[![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white)](https://databricks.com/)
[![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)
[![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=for-the-badge&logo=apache-spark&logoColor=white)](https://spark.apache.org/)
[![Delta Lake](https://img.shields.io/badge/Delta_Lake-00ADD8?style=for-the-badge&logo=delta&logoColor=white)](https://delta.io/)
[![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/features/actions)

*Pipeline ETL para integrar, transformar y analizar datos del ranking de empresas del Ecuador por la SUPERCIAS.*

</div>

---

## 🎯 Descripción

Este proyecto implementa un pipeline ETL con arquitectura de capas **Bronze → Silver → Gold** en Azure Databricks.

Fue desarrollado por **Jeremy Palma**, tomando como base una implementación completa de arquitectura medallion, empleando la fuente de datos del **ranking de empresas del Ecuador** publicado por la Superintendencia de Compañías, Valores y Seguros.

Todos los datos generados consideran la información de los **Estados Financieros** presentados bajo el estado de **compañías activas**.

Además, el análisis de estos datos permite tener una visión general del estado/salud de las empresas.

---

## ✨ Características principales

- 🔄 **ETL por capas**: Ingesta, transformación y carga analítica.
- 🏗️ **Arquitectura Medallion**: Separación clara de zonas Bronze, Silver y Gold.
- 📊 **Tablas analíticas**: Datos listos para explotación y visualización.
- ⚙️ **Automatización CI/CD**: Despliegue de notebooks con GitHub Actions.
- 🧾 **Gobierno y seguridad**: Notebooks de grants y revocación de permisos.

---

## 🏛️ Arquitectura del flujo

```text
Fuente HTTPS (SuperCias Ranking)
        ↓
🥉 Bronze: Ingesta de compañías, ranking, sector y segmento
        ↓
🥈 Silver: Estandarización y transformación
        ↓
🥇 Gold: Carga de datasets analíticos
        ↓
📈 Dashboard / consumo analítico
```

---

## 📁 Estructura del proyecto

```text
Proyect_Databricks_GitHub/
│
├── .github/
│   └── workflows/
│       └── deploy-notebook.yml                 # CI/CD de despliegue
├── process/
│   ├── Ingest_supercias_compania.ipynb         # Bronze: compañías
│   ├── Ingest_supercias_ranking.ipynb          # Bronze: ranking
│   ├── Ingest_supercias_sector.ipynb           # Bronze: sector
│   ├── Ingest_supercias_segmento.ipynb         # Bronze: segmento
│   ├── Transform_supercias.ipynb               # Silver: transformación
│   └── Load_supercias.ipynb                    # Gold: carga analítica
├── scripts/
│   └── Preparacion_Ambiente.ipynb              # Preparación de ambiente
├── security/
│   └── grants.ipynb                            # Asignación de permisos
├── reversion/
│   └── revoke.ipynb                            # Revocación de permisos
├── certifications/
│   └── credentials.png
├── DASHBOARD.png
├── ETL - DEV.png
├── ETL - DEV TAKS.png
├── ETL - PROD JOB RUN.png
└── README.md
```

---

## 🛠️ Tecnologías utilizadas

- **Azure Databricks** para ejecución del pipeline.
- **PySpark / Spark SQL** para transformación de datos.
- **Delta Lake** para persistencia confiable y transaccional.
- **GitHub Actions** para automatización de despliegue.

---

## ⚙️ Requisitos previos

- Cuenta de Azure con acceso a Databricks.
- Workspace de Databricks configurado.
- Repositorio GitHub con Actions habilitado.
- Configuración de credenciales para acceso a datos vía HTTPS y almacenamiento de destino.

---

## 🚀 Ejecución sugerida

1. Ejecutar `scripts/Preparacion_Ambiente.ipynb`.
2. Ejecutar notebooks de ingesta en `process/` (compañía, ranking, sector, segmento).
3. Ejecutar `process/Transform_supercias.ipynb`.
4. Ejecutar `process/Load_supercias.ipynb`.
5. Validar resultados en dashboard y/o tablas finales.

---

## 🔄 CI/CD

El flujo de integración continua se encuentra en:

- `.github/workflows/deploy-notebook.yml`

Este workflow automatiza el despliegue de notebooks para mantener sincronizado el entorno Databricks con el repositorio.

---

## 👤 Autor

**Jeremy Palma**

Proyecto orientado a ingeniería de datos con enfoque en automatización ETL y analítica empresarial sobre información oficial del ranking de compañías del Ecuador.

---

## 📄  **Referencia oficial de datos**
- Superintendencia de Compañías, Valores y Seguros (2023): https://appscvsmovil.supercias.gob.ec/ranking/reporte.html

