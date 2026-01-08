# Project AIRS: Automated Inventory Replenishment System

> **Zero-Budget ERP & Decision Engine for 200+ Vending Machines** > *Built with Python, Applied Mathematics, and Generative AI.*

## Overview
Project AIRS is a proprietary **Inventory Optimization System** architected to replace manual supply chain workflows. It acts as a "Decision Engine" for a network of **200+ vending machines**, automating the end-to-end process from data ingestion to route planning.

This project demonstrates the power of **AI-Augmented Development**—leveraging LLMs to rapidly translate complex Operations Research logic into enterprise-grade Python solutions.

## Key Features
- **Smart "Skip" Logic & Data Imputation:** The system calculates projected burn rates to actively recommend **skipping replenishment** (JIT) if stock suffices. It automatically injects **"Virtual Inventory Nodes"** (synthetic data) to bridge data gaps and maintain time-series continuity for the SES model.
- **SKU Graveyard & Opportunity Cost Tracker:** Automatically identifies underperforming "Zombie SKUs" for replacement. Upon delisting, the system archives their historical performance (Sales Velocity) to quantify the **Opportunity Cost**, creating a baseline to validate if the new replacement product generates higher ROI.
- **Prescriptive Advisor:** Analyzes sales velocity to recommend **Slot Expansion** (Planogram Optimization) and **Delisting**.
- **Dynamic Cap Logic:** Implements **Asymmetric Loss Functions** to balance Stockout Risk vs. Spoilage Waste.
- **Closed-Loop Efficiency Checker:** Automatically backtests forecast accuracy, calculating an "Efficiency Score" for every cycle.

## Technology Stack
- **Core Logic:** Python (Pandas, NumPy)
- **Math Models:** Simple Exponential Smoothing (SES), Stochastic Processes, Z-Score Safety Stock
- **Data Source:** Custom ETL Pipeline for Legacy ERP Data
- **Output:** Automated Excel SOPs for Field Drivers

## Impact
- **30% Reduction in Driver Field Hours:** Streamlined physical replenishment via "Smart Skip" logic and binary SOPs, significantly cutting time spent on-site.
- **60% Reduction** in weekly route planning man-hours.
- **90%+ Service Level** maintained across the network.
- **Zero IT Cost** implementation using open-source tools.

---
*Note: Sensitive proprietary data has been sanitized for this public demonstration.*
