# SAP S/4HANA Finance Global Template Implementation Blueprint

This repository contains a production-ready, enterprise-grade configuration workbook and implementation blueprint for a global deployment of SAP S/4HANA Finance. It serves as a comprehensive portfolio piece showcasing end-to-end organizational design, parallel financial ledger alignment, Business Partner master integration (CVI), cross-module integrations, and unit business process validation scripts.

---

## 🏢 Business Scenario Framework
The blueprint maps a greenfield implementation for **Mahayana Global Technology GMBH**, a multinational organization operating manufacturing, global engineering, and shared services branches across multiple currencies and local statutory tax rules.

* **Global Parent Entity:** Mahayana Global Technology GMBH (Group Consolidation Currency: `USD`)
* **Operating Companies:** * **`M001`**: MAHAYANA India Mfg Pvt Ltd (Primary Manufacturing - Location: Mumbai | Local Currency: `INR`)
  * **`M002`**: MAHAYANA India Services Ltd (R&D and Global Shared Services - Location: Bangalore | Local Currency: `INR`)
  * **`M003`**: MAHAYANA Germany GmbH (High-Precision Engineering & Sales - Location: Stuttgart | Local Currency: `EUR`)

---

## ⚖️ Parallel Ledger & Currency Architecture
To manage group reporting alongside divergent local country statutory tax requirements, a parallel ledger methodology is established within Controlling Area `MACO` (Utilizing Currency Type `30` - Group Currency in `USD`):

1. **Leading Ledger (`0L`):** Utilized for global group-level reporting. Standardized uniformly across all company codes using Fiscal Year Variant **`K4`** (January to December).
2. **Non-Leading Ledger (`L1`):** Activated explicitly for local regulatory reporting in India (`M001` & `M002`) to comply with the Indian Fiscal Year Variant **`V3`** (April to March).

---

## 📁 Repository Navigation Directory
Click any of the structural data modules below to examine the normalized configuration tables, transaction parameters, and database matrices:

1. [**`01_Enterprise_Structure.csv`**](./01_Enterprise_Structure.csv)
   * Core architectural definition of the enterprise framework, technical assignment keys, corporate currency designations, and parallel ledger associations.
2. [**`02_Baseline_Configuration_Steps.csv`**](./02_Baseline_Configuration_Steps.csv)
   * An execution sequence checklist mapping transaction codes (T-Codes) and exact implementation menu paths inside the SAP Customizing IMG.
3. [**`03_Business_Partner_Master_Data.csv`**](./03_Business_Partner_Master_Data.csv)
   * S/4HANA Business Partner design blueprints, specifying Customer-Vendor Integration (CVI) rules, number ranges, role extensions (`FLVN00`/`FLCU01`), and grouping switches.
4. [**`04_Chart_of_Accounts_&_FSV.csv`**](./04_Chart_of_Accounts_&_FSV.csv)
   * The complete Operative Chart of Accounts (**`MAOP`**) structure mapped vertically into a rigorous Financial Statement Version (FSV) node hierarchy with strict numeric account blocks.
5. [**`05_Banking_&_APP_Config.csv`**](./05_Banking_&_APP_Config.csv)
   * House Bank matrices, account limitations, and clearing rules designed to govern the Automatic Payment Program (APP / `F110` via transaction `FBZP`).
6. [**`06_FI_MM_Integration.csv`**](./06_FI_MM_Integration.csv)
   * The logistics valuation and automatic account determination matrix linking Materials Management to the Financial ledger via transaction code **`OBYC`** (**BSX**, **WRX**, and **PRD** keys).
7. [**`07_FI_SD_Integration.csv`**](./07_FI_SD_Integration.csv)
   * Order-to-Cash integration mappings defining Sales Organizations, distribution logistics units, and conditions assigned to revenue G/Ls via transaction code **`VKOA`** (**ERL** and **ERS** keys).
8. [**`08_Functional_Test_Scripts.csv`**](./08_Functional_Test_Scripts.csv)
   * Business process testing matrix providing functional audit steps to validate multi-currency subledger updates against Cost Center and Profit Center accounting limits.

---

## 🚀 Key S/4HANA Capabilities Demonstrated
* **Customer-Vendor Integration (CVI):** Elimination of independent master tables through single-point BP group execution synchronization rules.
* **Unified Logistics Integrations:** Proper handling of valuation accounting triggers mapped natively to plant structures rather than dummy tracking blocks.
* **Financial Statement Version Structure:** Pristine reporting alignment that handles text wrapping strings seamlessly without breaking comma delimiter structures.
