# IoT Asset Bundle
**Fleet IoT – Databricks Medallion Asset Bundle**

A modular fleet **IoT pipeline** built on the **Databricks Medallion Architecture**. Inspired by telemetry systems, it simulates continuous fleet sensor data, processes it through **Bronze, Silver, and Gold layers**, and enriches the data using **SQL UDFs**. The project uses **Databricks Asset Bundles** for structured deployment.

---

## Project Structure

### `continuous_ingestion`
- EventHub-style simulator notebook using PySpark to generate continuous sensor data.
- Produces the raw Delta table that all pipelines ingest.

### `asset_bundle/bronze`
- Bronze pipeline YAML.
- Bronze ingestion notebook.

### `asset_bundle/silver`
- Silver pipeline YAML.
- Transformation notebook applying validations and UDFs.

### `asset_bundle/gold`
- Gold pipeline YAML.
- Notebook generating aggregated business metrics.

### `asset_bundle/functions`
- UDF pipeline YAML.
- Notebook defining all IoT enrichment functions.

### `dbx.yml`
- Root configuration file for Databricks Asset Bundles.

---

## Data Flow

### Continuous Ingestion
- Simulates real-time sensor events such as GPS, speed, engine & battery metrics, tire pressure, geofence activity, and auxiliary equipment states.
- Uses PySpark to continuously generate random data, mimicking EventHub streaming.

### Bronze Layer
- Ingests raw IoT telemetry into a structured Delta table.
- Preserves the original incoming schema and metadata.
- Acts as the immutable source for downstream layers.

### Silver Layer
- Cleans, validates, and enriches the Bronze data.
- Applies domain logic through SQL-based UDFs.
- Produces structured streaming tables ready for analytics.

### Gold Layer
- Generates business-focused outputs: performance metrics, daily summaries, alert counts, and vehicle health indicators.
- Designed for dashboards, reporting, and downstream analytics.

---

## UDF Logic (Used in Silver Layer)
- `IsOverSpeeding`
- `IsLowFuel`
- `TirePressureStatus`
- `EngineTempStatus`
- `VehicleRiskScore`

> These functions translate raw telemetry into interpretable classifications and risk indicators.

---

## Purpose
This repository demonstrates a clean, **production-aligned implementation** of a real-time **IoT pipeline** on Databricks.  
It is **inspired by telemetry systems**, highlighting **streaming ingestion**, **medallion architecture design**, **SQL UDF enrichment**, and **business metric creation** using a clear and maintainable bundle structure.
