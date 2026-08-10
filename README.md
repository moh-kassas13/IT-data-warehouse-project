
# MEDICAL CENTER IT WAREHOUSE MANAGEMENT SYSTEM

## 1. EXECUTIVE SUMMARY & PURPOSE
--------------------------------------------------------------------------------
This document provides a structured framework for interviewing IT Supervisors, 
Warehouse Managers, and Systems Administrators regarding the deployment of a 
Windows-based, SQL-driven Warehouse Management System (WMS). 

The application utilizes Blue Yonder enterprise patterns:
  - License Plate Number (LPN) tracking (Serial Number, MAC, Asset Tag)
  - Granular bin location modeling (Zone-Aisle-Rack-Bin)
  - Strict state-machine asset lifecycle controls
  - Department Cost Center chargeback accounting

## 2. STAKEHOLDER DISCOVERY QUESTIONNAIRE
--------------------------------------------------------------------------------

[A] INBOUND RECEIVING & TAGGING
1. How do hardware shipments currently arrive at the loading dock (bulk purchase 
   orders vs. individual ad-hoc requests)?
2. Are serial numbers and MAC addresses pre-provided by vendors via EDI/CSV 
   (Advanced Shipping Notice), or scanned manually upon dock entry?
3. What specific hardware inspection rules determine if an asset is placed in 
   'HOLD_CONFIG' versus immediately moved to 'AVAILABLE' stock?

[B] PHYSICAL LOCATION & BIN HIERARCHY
1. What is the precise layout of the IT storeroom (Zones, Aisles, Racks, Bins)?
2. Are high-value assets (Cisco Core Switches, Barco Medical Displays) restricted 
   to specific locked cages or secure zones?
3. What capacity limits exist per bin (e.g., maximum unit count threshold)?

[C] OUTBOUND REQUISITIONS & COST CENTER ALLOCATION
1. What is the process for clinical wards (ICU, ER, Surgery) to request hardware?
2. How are department cost-center codes (e.g., CC-2105 for ICU, CC-4012 for 
   Radiology) validated against hospital finance systems?
3. What rules govern EMERGENCY priority orders over standard FIFO pick queues?

[D] REVERSE LOGISTICS & HIPAA DATA SANITIZATION
1. What is the mandatory step-by-step workflow when hardware is returned from 
   a clinical area?
2. How are disk-wipe and HIPAA sanitization logs recorded in the system before 
   re-issuing hardware to general stock?
3. What financial/asset criteria dictate moving an item to 'SCRAPPED' state?

## 3. CORE DATA STRUCTURES & SQL TABLES
--------------------------------------------------------------------------------
- Warehouse_Locations    (location_id, zone_code, aisle, rack, bin, is_active)
- Item_Master            (item_id, sku, item_name, category, is_serialized)
- Inventory_Assets       (asset_tag, serial_number, mac_address, status, location_id, cost_center_code)
- Department_Requisitions(requisition_id, department_name, cost_center_code, priority_level, status)
- Inventory_Transactions (transaction_id, asset_tag, transaction_type, from_loc, to_loc, user, timestamp)
================================================================================

## 🛡️ License

This project is licensed under the [MIT_License](LICENSE). You are free to use, modify, and share this project with proper attribution.

## 🌟About Me

Hi there! I'm Mohammad Kassas. I'm a computer engineer who enjoys creating a variety of projects that improve people's livelihoods and everyday lives. 
