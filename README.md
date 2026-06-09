# SAP S/4HANA Finance Global Template Implementation Blueprint

This repository contains a production-ready, enterprise-grade configuration workbook and implementation blueprint for a global deployment of SAP S/4HANA Finance. It serves as a comprehensive portfolio piece showcasing end-to-end organizational design, parallel financial ledger alignment, Business Partner master integration (CVI), cross-module logistics links, Asset Accounting, automatic taxation engine mappings, and advanced electronic bank clearing networks.

---

## 🏢 Business Scenario Framework
The blueprint maps a greenfield template deployment for **Mahayana Global Technology GMBH**, a multinational enterprise operating manufacturing, global engineering, and shared services branches across multiple local statutory tax regimes and fiscal tracking structures.

* **Global Parent Entity:** Mahayana Global Technology GMBH (Group Consolidation Currency: `USD`)
* **Operating Companies:** * **`M001`**: MAHAYANA India Mfg Pvt Ltd (Primary Manufacturing - Location: Mumbai | Local Currency: `INR`)
  * **`M002`**: MAHAYANA India Services Ltd (R&D and Global Shared Services - Location: Bangalore | Local Currency: `INR`)
  * **`M003`**: MAHAYANA Germany GmbH (High-Precision Engineering & Sales - Location: Stuttgart | Local Currency: `EUR`)

---

## ⚖️ Parallel Ledger & Currency Architecture
To manage group-level management metrics alongside divergent local country statutory reporting schedules, a parallel ledger methodology is established within Controlling Area `MACO` (Utilizing Currency Type `30` - Group Currency in `USD`):

1. **Leading Ledger (`0L`):** Utilized for global corporate consolidation. Standardized uniformly across all company codes using Fiscal Year Variant **`K4`** (January to December).
2. **Non-Leading Ledger (`L1`):** Activated explicitly for local regulatory reporting in India (`M001` & `M002`) to handle compliance variations via the Indian Fiscal Year Variant **`V3`** (April to March).

---

## 📁 Repository Navigation Directory
Click any of the structural data modules below to examine the normalized configuration tables, transaction parameters, and database matrices:

1. [**`01_Enterprise_Structure.csv`**](./01_Enterprise_Structure.csv)
   * Core architectural definition of the enterprise framework, technical assignment keys, corporate currency designations, and parallel ledger associations.
2. [**`02_Baseline_Configuration_Steps.csv`**](./02_Baseline_Configuration_Steps.csv)
   * An execution sequence checklist mapping transaction codes (T-Codes) and exact implementation menu paths inside the SAP Customizing IMG (Extended from step 1 to step 26).
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
9. [**`09_Asset_Accounting_Depreciation.csv`**](./09_Asset_Accounting_Depreciation.csv)
   * Fixed asset configuration blueprint allocating asset classes, useful life conditions, and accounting determination paths for SLM/WDV depreciation methodologies.
10. [**`10_Taxation_&_Special_GL_Config.csv`**](./10_Taxation_&_Special_GL_Config.csv)
    * Mapping matrices managing indirect taxation rules (CGST/SGST/IGST input and output condition tags) alongside Special G/L indicators governing advance down payments (`OBYR`/`OBXR`).
11. [**`11_EBS_Electronic_Bank_Statement.csv`**](./11_EBS_Electronic_Bank_Statement.csv)
    * Electronic reconciliation interface logic matching external transaction data stream keys (such as `NCHG` bank expenses or `NTFR` electronic clearing) directly to automated subledger posting variants.
12. [**`12_DMEE_&_IDoc_Integration.csv`**](./12_DMEE_&_IDoc_Integration.csv)
    * Outbound monetary file definitions via extended DMEEX XML format tree mappings (`SEPA_CT`) alongside inbound cross-application asynchronous ALE/IDoc partner profiles (`WE20`).

---

## 🚀 Key S/4HANA Capabilities Demonstrated
* **Customer-Vendor Integration (CVI):** Elimination of legacy independent master tables through single-point BP role synchronization switches.
* **Unified Logistics Account Determination:** Multi-currency automation paths linking operations natively to active plant valuation groups rather than tracking tables.
* **Parallel Financial Accounting Foundations:** Structural database configuration tracking group consolidation targets alongside regional fiscal variances seamlessly.
