# Cosmetics-Inventory-FEFO-Risk
An inventory analytics dashboard built to monitor batch-level expiry risks, FEFO (First Expired, First Out) compliance rates, and inventory valuation for cosmetic and skincare retail operations.


# Project Background
# Data Structure Overview
The project architecture mirrors an enterprise Warehouse Management System (WMS) across six dedicated worksheets in Cosmetics-Inventory-FEFO-Risk.xlsx:
1. DASHBOARD: An executive control panel capturing high-level performance indicators (KPIs), batch compliance ratios, category turnover balances, and expiration risk distributions.
2. MASTER_DATA: The primary relational inventory table (320+ batch records) linking product SKUs, batch IDs, inbound receipt dates, shelf-life expiry dates, unit cost structures, inbound/outbound volumes, and remaining stock balances.
3. Inbound_Batch: A granular log of 320+ inbound batch receipts tracking product categories (Cleanser, Makeup, Moisturizer, Serum, Sunscreen, Toner), total inbound values, and real-time days-to-expiry metrics.
4. Outbound_Orders: A transactional log tracking outbound sales order demands (ORD-5001 onwards), dispatch dates, requested SKU codes, and order quantities.
5. Analysis_FEFO: A logic-driven allocation engine that evaluates real-life outbound dispatches against FEFO rules, verifying whether fulfilled batches complied with the earliest expiration principle (Compliant vs Non-Compliant) and calculating Cost of Goods Sold (COGS).
6. PIVOT: Summary aggregation layers aggregating inbound volumes, outbound fulfillment, remaining balances, and category-level cost variances.

Ps: The dataset used in this repository (Cosmetics-Inventory-FEFO-Risk.xlsx) comprises simulated/dummy inventory and shipment data created exclusively for portfolio and technical demonstration purposes.

# Executive Summary
<img width="1440" height="1066" alt="FEFO Dashboard_page-0001 (1)" src="https://github.com/user-attachments/assets/ab034713-dedf-47e8-a232-2a2ea0fa92e4" />

An analysis of the simulated portfolio data (320+ batches across 6 core cosmetic categories) reveals key supply chain metrics:
1. Total Inventory Asset Value: Total inbound stock valuation across the portfolio stands at Rp 4,210,550,000 (Rp 4.21 Billion), representing 114,800 units received.
2. Current Holding & Dispatches:
A. Outbound Dispatches (Realised Demand): 36,950 units dispatched across 80+ sales orders, generating a total COGS value of Rp 776,450,000.
B. Remaining Stock Balance: 77,850 units remaining in warehouse storage.
C. FEFO Dispatch Compliance Rate: Outbound batch dispatch compliance stands at 18.75% Compliant vs 81.25% Non-Compliant. A significant proportion of outbound orders were fulfilled using newer batches rather than the nearest-to-expiry stock, indicating substantial operational deviations from FEFO protocol.
4. Expiration Risk Profile:
A. Expired / Critical Risk (< 0 Days): Approximately 9.41% of remaining stock value is attached to expired or near-expiry batches.
B. Category Concentration: Cleanser and Toner lines represent the highest throughput volumes (23,600 and 23,650 units received, respectively), whilst high-value Moisturizers and Serums contain the largest capital tied up in slow-moving batches.

# Strategic Recommendations
Based on the empirical findings from the FEFO analysis, the following operational strategies are recommended:
1. Systematically lock WMS picking processes so warehouse staff are physically directed to pick the oldest expiring batch (Analysis_FEFO), eliminating the 81.25% non-compliance rate in order fulfillment.
2. Immediately liquidate or discount batches with fewer than 90 days to expiry (particularly high-cost Moisturizer and Retinol lines) to recover capital before mandatory write-off thresholds.
3. Implement automated dynamic threshold alerts (e.g., 180-day, 90-day, and 30-day expiry triggers) on the Inbound_Batch tracking sheet to notify sales and marketing teams well in advance of batch obsolescence.
4. Re-evaluate purchase order quantities for slow-turning categories (Serum lines) to align inbound replenishment cycles with actual outbound demand rates (Outbound_Orders), reducing safety stock holding times.



