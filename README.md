# Zero-Budget Inventory AI (The "Micro-ERP")

> **An autonomous, algorithm-driven inventory management system developed to optimize vending machine operations with zero recurring SaaS costs.**

## 📖 Overview
Managing inventory for distributed retail points (vending machines) typically requires expensive ERP software or results in significant inefficiency via manual guessing.

This project is a **Python-based "Micro-ERP"** built from scratch to solve the "Travelling Salesman Problem" of inventory: **What exactly should a driver carry to maximize sales while minimizing load and waste?**

It ingests raw historical data, applies **Exponential Smoothing (SES)** for demand forecasting, and uses a **Dynamic Policy Engine** to generate precise weekly replenishment plans.

---

## 🧠 System Architecture

The following logic flow represents how the system processes raw data into actionable decisions:

```mermaid
graph TD
    subgraph Input_Layer [DATA INGESTION]
        A[IMS.xlsx (Raw History)] -->|Parse Dates & Clean| B(Data Preprocessing)
        B -->|Identify Location Status| C{Status Check}
        C -->|New Location| D[Rookie Mode]
        C -->|Est. Date < Today| E[Overdue Handling]
        C -->|Normal| F[Mature Mode]
    end

    subgraph Core_Engine [THE BRAIN]
        direction TB
        
        %% Forecasting Module
        F --> G[Forecast Engine]
        G -->|Calculate EWMA / SES| H(Predicted Velocity)
        G -->|Sparse Data Penalty| I(Blind Spot Correction)
        
        %% Policy Module
        D --> J[Policy Engine]
        H --> J
        J -->|Category Constraints| K{Category Type}
        K -->|Chips| L[Dynamic Cap (4 vs 8)]
        K -->|Bakery/Choco| M[Safety Net Limits]
        
        %% Decision Logic
        J -->|Current Stock - Burn Rate| N[Replenishment Decision]
        N -->|Output| O(Qty to Carry)
        
        %% Feedback Loop
        O --> P[Shadow Ledger (JSON)]
        P -->|Virtual Stock Tracking| B
    end

    subgraph Audit_Layer [EFFICIENCY & INSIGHTS]
        Q[Efficiency Checker] -->|Backtest Last Refill| R[Calculate Asymmetric Loss]
        R -->|Over-Carry| S(Waste Score)
        R -->|Under-Carry| T(Missed Sales Score)
        
        U[Operations Advisor] -->|Analyze Trends| V(Hot/Cold Alerts)
    end

    subgraph Output_Layer [ACTIONABLE INTELLIGENCE]
        O --> W[Weekly_Plan.xlsx]
        V --> W
        S --> W
        T --> W
    end

    %% Connect Auditor
    F --> Q
