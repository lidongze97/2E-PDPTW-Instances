# Benchmark Instances for the 2E-PDPTW
This repository contains the comprehensive benchmark dataset for the **Two-Echelon Pickup and Delivery Problem with Time Windows (2E-PDPTW)**. 

These instances are designed to simulate realistic urban logistics operations involving both short-haul (intra-district) and long-haul (inter-district) transportation demands, strictly requiring first-echelon (FE) consolidation and temporal synchronization.

## 📦 Instance Characteristics

The dataset extends the classical Solomon (1987) VRPTW benchmark scheme into a two-echelon pickup-and-delivery network. It features 180 instances categorized into three spatial configurations: **C (Clustered), R (Random), and RC (Random-Clustered)**.

### Key Features:
- **Spatial Distribution**: 
  - **C-type**: 60% intra-satellite pairs, 40% inter-satellite pairs.
  - **RC-type**: 20% intra-satellite pairs, 40% inter-satellite pairs, 40% randomly distributed pairs.
- **Scale**: Number of customers $|V^C| \in \{30, 40, 50\}$, number of satellites $|V^S| \in \{3, 4\}$.

## 🗂️ Naming Convention

Each instance file is named in the format `[Class][Index]_[Customers]_[Satellites].csv`.
For example, `C1_30_3.csv` indicates:
- **C1**: Clustered distribution pattern (Group 1)
- **30**: Total number of customer nodes (15 pickups + 15 deliveries)
- **3**: Number of satellites

## 📄 Data Format

The `.csv` files are structured with the following columns:
`NODE_ID, XCOORD, YCOORD, DEMAND, READY_TIME, DUE_DATE, SERVICE_TIME`

### Node Indexing Rules:
To facilitate algorithmic implementation (e.g., Branch-and-Price-and-Cut), the nodes are strictly indexed as follows:
- **Satellites**: Indicated by `S1, S2, S3, ...` (Virtual origin/destination copies have been removed for raw data clarity).
- **Pickups & Deliveries**: The first half of the numeric nodes represent **pickup locations**, and the second half represent their corresponding **delivery locations**. 
  *(e.g., in a 40-customer instance, nodes 1-20 are pickup points, and nodes 21-40 are their exact corresponding delivery points, where node `i + 20` is the delivery for pickup `i`).*


Global parameter settings used in our baseline evaluations:
- FE vehicle capacity ($Q^1$): 300
- SE vehicle capacity ($Q^2$): 100
- FE fixed fleet cost ($f^1$): 25
- SE fixed fleet cost ($f^2$): 15
