# SAP MM Procurement Internship: Rigel case study

Work for the YuvaIntern **SAP MM Procurement Specialist** virtual internship (9 Nov to 21 Dec 2026) by Pawan Singh Kapkoti.

Each week's report studies an SAP MM topic with **Rigel ERP** as the case: an ERP for small Indian traders and fabrication workshops that I build. Each week I also build the matching procurement feature in Rigel and describe it in that week's report. Rigel's source code is private; this repository holds the reports, diagrams and screenshots from Rigel's demo company (no real business data).

## Weeks

| Week | Dates | SAP MM topic | Feature built in Rigel | Report |
| --- | --- | --- | --- | --- |
| 1 | 9 to 15 Nov | Strategic procurement planning | Three-way match: PO, goods receipt (GRN) and supplier invoice compared, Matched or Difference | [week-1](week-1/) |
| 2 | 16 to 22 Nov | Vendor evaluation and selection | Supplier score from on-time delivery, fill rate, damage and price change | [week-2](week-2/) |
| 3 | 23 to 29 Nov | Master data management | Reasons for damaged goods on a GRN | [week-3](week-3/) |
| 4 | 30 Nov to 6 Dec | Procurement execution | Purchase order approval above an amount | [week-4](week-4/) |
| 5 | 7 to 13 Dec | Reporting and analytics | Reorder to PO, and materials to buy from open orders | [week-5](week-5/) |
| 6 | 14 to 21 Dec | Post-procurement review | Review and improvements | [week-6](week-6/) |

## SAP MM and Rigel at a glance

| Step | SAP MM | Rigel |
| --- | --- | --- |
| Request | Purchase requisition (ME51N) | None yet; approval above an amount in week 4 |
| Order | Purchase order (ME21N) | Purchase order, emailed to the supplier, who accepts on a link |
| Supplier ships | Advance shipping notice | Supplier records the dispatch, in parts, on the same link |
| Receive | Goods receipt (MIGO, movement 101) | GRN: received and damaged per line, damaged goods to an on-hold bin |
| Invoice check | Logistics invoice verification (MIRO), three-way match | Three-way match on the GRN (week 1) |
| Return | Return delivery, credit memo | Debit note, then the supplier's credit note recorded against it |
| Pay | Payment run (F110) | Payments recorded by hand, in parts, against each GRN |
