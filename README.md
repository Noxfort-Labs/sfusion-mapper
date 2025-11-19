<div align="center">

<img src="assets/icon/logo.png" alt="SFusion Mapper Logo" width="120"/>

# SFusion Mapper
### Zero-Day ETL Configuration Utility

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Python](https://img.shields.io/badge/Python-3.12-yellow.svg)](https://www.python.org/)
[![Qt](https://img.shields.io/badge/Framework-PySide6-green.svg)](https://doc.qt.io/qtforpython/)
[![Build](https://img.shields.io/badge/Build-Docker%20%7C%20PyInstaller-blue)](https://www.docker.com/)

</div>

---

## 📖 Overview

**SFusion Mapper** is a specialized graphical utility designed for the **Noxfort Labs SFusion ecosystem**. It serves as the "Zero Day" configuration tool, bridging the gap between raw network topology data and the core ETL (Extract, Transform, Load) engine.

The application allows data engineers to visualize complex network maps, semantically rename elements, and associate heterogeneous data sources (CSV, JSON, Excel) to specific network nodes and edges. The output is a consolidated **SQLite database (.db)** that acts as the instruction set for the SFusion ETL pipeline.

## ✨ Key Features

* **Topology Visualization:** High-performance rendering of SUMO network maps (`.net.xml` / `.net.xml.gz`) using the Qt Graphics View Framework.
* **Heterogeneous Data Sources:** Import and analyze data schemas from various formats (`.csv`, `.json`, `.xml`, `.xlsx`).
* **Visual Association:** Interactively link local data sources to specific map elements (Edges/Streets or Nodes/Junctions).
* **Metadata Enrichment:** User-friendly editor to assign "Real Names" to cryptic technical IDs (e.g., renaming edge `-238492` to `Main Avenue`).
* **Project Management:** Save and load work-in-progress states using the JSON-based Project format (`.sfm.json`).
* **Optimized Export:** Generates a portable `.db` file containing all mappings and metadata for downstream processing.

## 🏗️ Technical Architecture

SFusion Mapper is built with **Python 3.12** and **PySide6 (Qt6)**, strictly adhering to the **Model-View-Controller (MVC)** design pattern and the **Single Responsibility Principle (SRP)**.

### Core Layers
1.  **Model (`src/domain`):** Pure data entities (`MapNode`, `MapEdge`, `DataSource`) and the application state manager (`AppState`), acting as the Single Source of Truth.
2.  **View (`ui/`):** Passive UI components (`MapView`, `SourcesPanel`, `EditorPanel`) that display data and emit signals.
3.  **Controller (`src/controllers`):** Orchestrates logic, bridging user interactions in the View with data updates in the Model.
4.  **Services (`src/services`):** Dedicated workers for heavy I/O operations (XML parsing via `lxml`, Data analysis via `pandas`, SQLite persistence), executed in background threads to ensure UI responsiveness.

## 🚀 Installation & Usage

### Option 1: Installing the Debian Package (Recommended)
If you have the `.deb` installer:

```bash
sudo apt install ./sfusion-mapper_0.1.0_amd64.deb
sfusion_mapper
