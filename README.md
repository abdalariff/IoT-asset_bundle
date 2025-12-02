# telemetry-asset_bundle
Telemetry Asset Bundle – Fleet Medallion Pipeline

This repo implements a complete Databricks Medallion Architecture (Bronze → Silver → Gold) for real-time fleet telemetry. It ingests continuous sensor data, cleans and enriches it with SQL UDFs, and produces analytics-ready Gold tables.

🚗 What This Bundle Does

Ingests streaming fleet sensor events

Adds metadata + raw history (Bronze)

Cleans, validates, and enriches with UDF logic (Silver)

Aggregates KPIs like speed, distance, fuel, risk score (Gold)

Easily deployable via Databricks Asset Bundles

🧱 Pipeline Layers
Bronze

Raw FleetSensorEvents

Adds ingest timestamp + source system

Silver

Applies UDFs: overspeed, fuel check, tire pressure, temperature status, risk score

Standardizes + cleans data

Gold

Vehicle-level metrics

Hourly/daily aggregates

Geofence, speed, fuel, engine KPIs

🔧 UDFs Included

IsOverSpeeding

IsLowFuel

TirePressureStatus

EngineTempStatus

VehicleRiskScore

🚀 Deploy

Use Databricks Asset Bundles:

databricks bundle deploy
databricks bundle run fleet_medallion_pipeline

📌 Purpose

A clean, modular example of real-time telemetry ETL, designed for:
Fleet data, IoT pipelines, alerting, KPI dashboards, ops intelligence.
