# Creating a Custom Table in SAP ABAP Dictionary (DDIC) — ZCUSTOMER_TABLE

This README documents the steps captured in the screenshots for creating a custom transparent table `ZCUSTOMER_TABLE` in the SAP ABAP Dictionary (transaction **SE11**).

## Overview

**Table Name:** `ZCUSTOMER_TABLE`
**Short Description:** Customer detail Table in DDIC
**Table Type:** Transparent Table

## Steps

### 1. Open ABAP Dictionary Initial Screen
- Go to transaction **SE11**.
- Select the **Database table** radio button.
- Enter the table name `ZCUSTOMER_TABLE`.
- Click **Create**.

### 2. Set Short Description
- On the **Attributes** tab, enter the short description: `Customer detail Table IN DDIC`.

### 3. Configure Delivery and Maintenance
Go to the **Delivery and Maintenance** tab and set:

- **Delivery Class:** `A` — Application table (master and transaction data)
  (Other available options include `C`, `L`, `G`, `E`, `S`, `W` for customizing/system tables.)
- **Data Browser/Table View Editing:** Choose from:
  - Display/Maintenance Allowed with Restrictions
  - **Display/Maintenance Allowed** *(selected)*
  - Display/Maintenance Not Allowed
  - Only display allowed

### 4. Define Fields
Go to the **Fields** tab and add the table fields with their data elements:

| Field       | Key | Initial | Data Element | Data Type | Length | Short Description       |
|-------------|-----|---------|---------------|-----------|--------|--------------------------|
| ZNAME       | ✔   | ✔       | ZNAME         | CHAR      | 50     | Name of the account holder |
| ZCUST_ID    | ✔   | ✔       | ZCUST_ID      | CHAR      | 4      | Customer Id              |
| ZADRESS     |     |         | ZADRESS       | CHAR      | 30     | ADDRESS                  |
| ZCONTACT    |     |         | ZCONTACT      | CHAR      | 10     | Contact details          |

- `ZNAME` and `ZCUST_ID` are marked as **Key** fields.
- Each field is linked to its own **Data Element** (e.g., `ZNAME` data element is built on the **Built-in type** `CHAR`, length `50`).

### 5. Define Technical Settings
Access via **Technical Settings** button:

- **Data Class:** choose from options such as:
  - `APPL0` – Master Data, Transparent Tables
  - `APPL1` – Transaction Data, Transparent Tables
  - `APPL2` – Organization and customizing
  - `DDIM` – Dimension Tables in BW
  - `DFACT` – Facts Table in BW
  - `DODS` – ODS Tables in BW
- **Size Category**
- **Buffering Settings:** Buffering Not Allowed / Buffering allowed but switched off / Buffering Activated
- **Data Changes:** Option to enable **Log Changes**

### 6. Save & Activate
- Saving the table adds it to a list of **Inactive Objects** pending activation, alongside other related objects in the same package/request, e.g.:
  - `ZCDS_EKKO` (DDLS)
  - `ZI_PO_ITEM` (DDLS)
  - `ZSALES_REPORT` (TABL)
  - `ZCUSTOMER_TABLE` (TABL)
  - `ZCDS_EKKO` (TABL)
  - `ZVENDERDETAIL` (TABL)
- Activate the object to make it usable.

### 7. Test via Data Browser (SE16)
- Once activated, the table can be accessed via the **Data Browser: Table ZCUSTOMER_TABLE: Selection Screen**.
- Selection fields available: `ZNAME`, `ZCUST_ID`, `ZADRESS`, `ZCONTACT` (each with a "to" range).
- Additional options: **Width of Output List** (default 250), **Maximum No. of Hits** (default 200).

## Summary

This walkthrough demonstrates the end-to-end process of creating a Z-custom transparent table in SAP's ABAP Dictionary — from initial creation, setting delivery/maintenance rules, defining fields and data elements, configuring technical/buffering settings, activating the table, and finally verifying it through the Data Browser.
