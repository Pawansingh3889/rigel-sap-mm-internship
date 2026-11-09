# Strategic Procurement Planning in SAP MM: A Small Indian Steel Workshop and Rigel ERP

Pawan Singh Kapkoti

YuvaIntern SAP MM Procurement Specialist, Week 1

November 2026

## 1 Executive summary

A workshop cannot finish a fabrication job if the right steel is missing, even when its purchase register looks complete. Procurement must connect the requirement, supplier commitment, physical receipt and payment. In this report, I propose a procurement plan for a hypothetical Indian steel fabrication workshop with about 25 people, annual turnover of about Rs 6 crore and approximately 30 suppliers. It buys steel sections, plates, fasteners and paint. These are case assumptions, not details of a real customer.

I use standard SAP MM practices to build the plan and compare each stage with Rigel ERP, which I build for small Indian traders and fabrication workshops. SAP provides structured purchasing, stock control, invoice verification and integration with finance and production. Rigel applies selected controls through simpler documents and supplier participation. The comparison explains both the shared principles and the differences in capability.

My strategy starts with reliable material and supplier records, then introduces planned buying, documented approvals, receipt checks and timely settlement. A 12-week rollout gives purchasing, stores, accounts and production clear responsibilities. Proposed targets cover delivery reliability, invoice differences, price changes, shortages, damage and payment deadlines. They are management targets to test against a baseline, not claimed improvements.

The Week 1 Rigel feature is three-way matching on the goods receipt note, or GRN. It compares the supplier invoice total with the receipt value and separately shows each receipt line's rate against its purchase order. It warns without blocking receipt or part payment. I explain why this suits a small workshop, while keeping review and accountability essential.

## 2 Organization and procurement goals

The hypothetical workshop makes fabricated steel items against customer requirements. I assume one purchasing employee, a stores function, an accounts employee and an owner who also oversees operations. Production staff identify material needs. Some people cover more than one role, so the plan must work without a large purchasing department.

Steel grade, section size, plate thickness and unit of measure matter as much as price. A cheaper item with the wrong specification can delay the entire job. Fasteners need consistent dimensions and grades; paint needs the specified type and quantity. Procurement should preserve these distinctions in both SAP and Rigel.

I propose six measurable goals for the end of rollout. Weeks 1 and 2 establish the starting position from available documents. Missing historical evidence is marked unavailable rather than reconstructed as fact.

| Goal | Proposed target by week 12 | Reason |
| --- | --- | --- |
| Reliable delivery | At least 95% of due delivery lines received on time | Protect promised production dates |
| Invoice accuracy | No more than 5% of checked GRNs show an invoice total difference above Rs 1 | Reduce avoidable billing disputes |
| Price discipline | No more than 2% weighted absolute receipt rate variance against PO rates | Expose unplanned changes in buying cost |
| Material availability | No more than one production stoppage caused by material shortage in four weeks | Keep fabrication work moving |
| Receipt quality | Damaged share no greater than 2% within each comparable material group and unit | Avoid unusable stock and rework |
| Timely supplier payment | 100% of covered micro and small supplier dues paid by the applicable deadline | Protect compliance and supplier trust |

These targets do not justify buying excess stock or accepting inferior steel. I would review performance with the owner every week and explain exceptions by material and supplier. If a target proves unrealistic, the owner should approve a revised target after reviewing evidence. The original target remains visible so that the team cannot improve results simply by changing definitions.

## 3 Key challenges today

For this case, I assume the workshop currently mixes notebooks, spreadsheets, calls and WhatsApp orders. These are hypothetical starting conditions. A verbal agreement may contain the latest price, while the spreadsheet still holds the old one. A supplier can believe an order is confirmed before production has settled the specification.

Bills are not consistently checked against receipts. Accounts may see an invoice for 100 rods while stores has received only 95. A separate price increase can hide inside the same invoice. Partial deliveries make this harder because one order can remain open across several receipts and payments.

Damaged steel creates another gap between physical stock and usable stock. Rust, bent sections or transport damage should not silently enter the material available for production. Without a recorded location and return trail, rejected goods can be counted as available or paid for without follow-up.

Steel price swings encourage urgent buying, but buying too much ties up cash and storage space. Supplier concentration can also turn a transport delay or a supplier's capacity problem into a production stoppage. The owner needs alternatives before an emergency occurs.

Payment planning must account for the MSME rule accurately. For covered micro and small suppliers, the written payment agreement cannot extend beyond 45 days from acceptance or deemed acceptance; without such an agreement, the relevant period is 15 days. A general 45-day watch therefore needs an accounts check for earlier deadlines. This distinction follows the [public MSME guidance](https://odr.msme.gov.in/assets/pdf/MSE_Scheme_on_ODR_for_Delayed_Payment_Guidelines.pdf).

Finally, the same employee may order, receive and arrange payment. I would separate these checks wherever staffing permits and require owner review where it does not. Software records support this responsibility; they do not replace it.

## 4 The procurement cycle from planning to execution

My approach follows SAP's public documentation and common practice: plan demand, maintain sources, authorize buying, record receipts, verify invoices and review results. Modern procurement also means managing exceptions early and letting suppliers communicate commitments. SAP S/4HANA supports integrated business processes, while Ariba supports broader sourcing and supplier collaboration. Neither is a required purchase for this hypothetical workshop.

**4.1 Establish material and supplier records**

In SAP, MM01 creates the material master with the information needed by purchasing, inventory and planning. The business partner or vendor master identifies the supplier and relevant purchasing and payment details. ME11 creates a purchasing info record for the material and supplier relationship, including purchasing conditions. ME01 maintains the source list; quota arrangements can distribute requirements among approved sources.

In Rigel, supplier price lists support price reference and comparison. I would first standardize material names, units and supplier records, then compare price lists for equivalent specifications. This is a data preparation task, not a claim that Rigel has SAP source lists or quota arrangements. One named buyer owns corrections and asks stores to confirm units before use.

**4.2 Plan requirements**

SAP material requirements planning, or MRP, compares requirements with stock and expected receipts. MD01 runs planning and MD04 shows the stock and requirements situation. Relevant lead times and planning settings determine when procurement proposals are needed. I would begin with frequently used steel and fasteners, then extend the scope once records are dependable.

In Rigel, the current stock ledger and open purchasing documents support a buyer's review. Reorder to PO and materials to buy from open orders are planned for Week 5. Until then, the buyer and production supervisor manually agree the requirement, required date and available usable stock. On-hold damaged stock must not satisfy that requirement.

**4.3 Request and authorize the purchase**

SAP ME51N creates a purchase requisition. A release strategy can require approval according to configured conditions before purchasing proceeds. The workshop's request should state the material, quantity, required date and job or operational purpose. Approval should confirm need and spending responsibility, not merely repeat data entry.

Rigel has no separate requisition stage in this case. The proposed interim control is a documented request reviewed by the buyer and owner. Week 4 will introduce PO approval above Rs 50,000 by the owner or a manager. I do not treat that future control as available during Week 1.

**4.4 Compare suppliers and select a source**

SAP supports requests for quotation through ME41, quotation entry through ME47 and price comparison through ME49. I would compare specification, price, delivery date, freight, payment terms and previous quality. For recurring purchases, contracts created through ME31K and scheduling agreements through ME31L provide outline agreements suited to different supply arrangements.

In Rigel, the buyer uses supplier price lists and existing delivery and quality reports, with a documented manual comparison where necessary. There is no claimed equivalent to every SAP sourcing transaction. For critical steel sizes, I propose a qualified alternate supplier and occasional trial orders. The lowest quoted rate should not win when delivery or material suitability is uncertain.

**4.5 Create the order and obtain commitment**

SAP ME21N creates the purchase order with agreed quantities, conditions and delivery requirements. The buyer checks that the PO reflects the approved source and commercial agreement. Repeated requirements can draw on the appropriate outline agreement rather than renegotiating every purchase from scratch.

Rigel emails the PO to the supplier. On the supplied link, the supplier accepts, declines or requests changes. This gives the buyer a clear response to follow up. A requested change still needs a purchasing decision; it should not be treated as acceptance of new terms merely because the supplier proposed it.

**4.6 Track dispatch and receive goods**

In the SAP process, purchasing follows expected deliveries and keeps the order history current. Stores posts goods receipt using MIGO, normally with movement type 101 against the PO. Partial receipts leave the remaining order quantity to be managed. Where inspection is configured, goods can enter quality inspection stock pending the quality decision.

Rigel lets the supplier record dispatches in parts on the same link, including an e-way bill and files. The GRN records received and damaged quantities per line, and damaged goods move to an on-hold bin. Dispatch information is evidence of shipment, not proof of receipt. Stores still counts and examines the goods when they arrive.

**4.7 Verify, return and settle**

SAP MIRO performs logistics invoice verification against purchasing and receipt information. Configured tolerance checks can result in a payment block. The GR/IR clearing account connects goods receipt and invoice receipt accounting. A return delivery can use MIGO movement type 122, followed by the appropriate supplier credit treatment. FI payment processing can use F110 for eligible due invoices.

Rigel requires the supplier invoice number and date on the GRN. This week's match adds a comparison with the supplier invoice total and a separate line rate comparison. Payments are recorded manually against the GRN and can be made in parts. Returns use a debit note, followed by the supplier's credit note recorded against it as Settled or Difference.

**4.8 Review and improve**

SAP ME2M and ME2N support purchasing review, MB52 shows warehouse stock and MB51 shows material documents. Vendor evaluation through ME61 supports structured assessment. Rigel reports purchase performance, prices, supplier delivery and damaged share. Its combined supplier score is planned for Week 2. I would review exceptions weekly and use evidence from completed orders when deciding future sourcing.

| Stage | SAP MM approach | Rigel case comparison |
| --- | --- | --- |
| Prepare | Masters, ME11, ME01, quota arrangement | Consistent records and supplier price lists |
| Plan | MD01 and MD04 | Manual review now; buying tools in Week 5 |
| Authorize | ME51N and release strategy | Interim review; PO approval in Week 4 |
| Source | ME41, ME47, ME49, outline agreements | Price lists, reports and buyer comparison |
| Order | ME21N | Emailed PO and supplier response link |
| Receive | MIGO 101 and inspection stock | GRN with damage sent to on-hold bin |
| Check and pay | MIRO, GR/IR and FI payment run | Warning on GRN and manual part payments |
| Return and learn | MIGO 122, credits and ME61 | Debit note, supplier credit and performance reports |

## 5 Three-way match in depth

Three-way matching asks three practical questions: what did I order, what did I receive and what did the supplier bill? These documents describe different events. Agreement between two does not prove that the third is correct.

**5.1 SAP invoice verification and accounting**

In SAP, MIRO uses PO and receipt information for logistics invoice verification. Configured tolerance keys distinguish checks such as price and quantity variances. An invoice can be posted yet blocked for payment when relevant upper tolerances are exceeded. A block requires review and resolution before payment eligibility is restored. This is configurable behavior, not a rule that every small difference stops every invoice. These principles are described in [SAP's public documentation](https://learning.sap.com/courses/invoice-verification-in-sap-s-4hana/entering-invoices-with-variances-1).

For an ordinary valuated stock purchase, goods receipt debits inventory and credits GR/IR. Invoice receipt debits GR/IR and credits the supplier liability, with taxes and differences handled through the applicable accounting configuration. GR/IR is a bridge between two events that may happen on different dates. Unbalanced items need investigation and reconciliation; invoice posting is not a promise that every item has automatically cleared. This role follows [SAP's public documentation](https://help.sap.com/doc/8353d7531a4d424de10000000a174cb4/700_SFIN3E%20006/en-US/f47fd1538cdf4608e10000000a174cb4.html).

For this workshop, I would configure relevant checks and test missing receipts, excess billed quantities, changed rates and partial deliveries before wider use. I would not set broad tolerances merely to make the exception list disappear.

**5.2 Rigel's two visible checks**

Rigel asks for the supplier invoice total on the GRN. The total comparison subtracts the GRN value from that amount. A difference within Rs 1 either way is Matched; a larger difference is shown as billed more or less than received. Without an invoice total to compare, the result is Not checked. Required invoice number and date do not themselves prove that the value was checked.

Separately, each line's receipt rate is compared with its linked PO rate. This matters because matching totals can still contain an unapproved price increase. The total match is therefore a useful signal, not proof of complete commercial or tax correctness. Amounts must be compared on a consistent basis, including any applicable taxes, charges and rounding.

**5.3 Worked example**

Assume no tax, freight, discount or damage in this example. The PO is for 100 rods at Rs 50. Only 95 arrive. The supplier bills 100 rods at Rs 52, so the invoice total is Rs 5,200. The receipt records the supplied rate of Rs 52.

| Check | Calculation | Result |
| --- | --- | --- |
| Original PO value | 100 x Rs 50 | Rs 5,000 |
| Supplier invoice | 100 x Rs 52 | Rs 5,200 |
| GRN value | 95 x Rs 52 | Rs 4,940 |
| Invoice less receipt | Rs 5,200 minus Rs 4,940 | Rs 260 |
| Rate increase | (Rs 52 minus Rs 50) / Rs 50 x 100 | 4% |

The GRN shows "Difference Rs 260: billed more than received" and the line shows "4% above the PO's Rs 50". Owed is Rs 4,940, payable in parts. The warning does not replace that amount with Rs 5,200 or change it to the original PO rate. The buyer must separately resolve the five missing rods and the higher rate.

**5.4 Why warn without blocking**

A small workshop often handles a partial delivery, a supplier conversation and a part payment on the same day. A warning lets stores record what arrived while the owner resolves the commercial issue. Rigel's match never blocks this workflow or part payments.

The tradeoff is reliance on human follow-up. I propose that accounts review every Difference and Not checked case before deciding payment, record the explanation and escalate unresolved cases to the owner. This is a proposed operating procedure, not an automatic Rigel payment block. A warning should preserve flexibility without becoming permission to ignore discrepancies.

## 6 Integration of SAP MM with other modules and the efficiency it brings

Procurement works best when one recorded event informs the next team. A receipt should update stock, help accounts verify the bill and tell production whether material is usable. SAP MM integration supports this shared view, provided master data, account assignments and process settings are correct.

| Module | Connection with SAP MM | Efficiency for the workshop | Rigel comparison |
| --- | --- | --- | --- |
| FI, Financial Accounting | Receipt and invoice postings, GR/IR, supplier liability and payment | Fewer gaps between stock records and accounts | GRN dues and part payments; no claimed SAP accounting equivalence |
| CO, Controlling | Procurement account assignments and consumption costs | Helps identify which job or cost center uses resources | Proposed manual review of purchasing costs by job where evidence is available |
| SD, Sales and Distribution | Customer demand informs material availability and procurement needs | Customer commitments consider material supply | Materials to buy from open orders is planned for Week 5 |
| PP, Production Planning | Production requirements feed MRP and purchasing proposals | Orders materials against production needs and lead times | Buyer and production review needs manually in the current plan |
| QM, Quality Management | Inspection at receipt and decisions on material use | Prevents unapproved material being treated as usable | GRN damage quantities and on-hold bin; damage reasons planned for Week 3 |
| WM, Warehouse Management | Warehouse movements and bin handling connect with inventory | Helps stores locate material and control placement | Document-driven stock ledger and bins |

I would keep the first implementation narrow. FI reconciliation, dependable receipts and communication with production bring immediate control. More detailed planning or warehouse processes should follow a real requirement, not a desire to reproduce every enterprise feature.

Rigel's strongest shared principle is document-based movement: stock lives in a ledger and moves only through documents. Nothing is deleted; documents are cancelled with a reason, and changes enter an audit log. This gives a small team a traceable sequence to investigate without claiming that Rigel contains every SAP module.

## 7 Risk analysis and mitigation

The ratings below are my planning judgments for the hypothetical workshop, not measured probabilities. High impact means production, cash or compliance could be materially affected. Each risk needs an owner and a review date even if a system provides a warning.

| Risk | Likelihood | Impact | Mitigation in SAP | Mitigation in Rigel and workshop procedure |
| --- | --- | --- | --- | --- |
| Supplier concentration | Medium | High | Approved source lists and quota arrangements across qualified sources | Buyer maintains an alternate; reviews delivery reports and trial orders |
| Steel price volatility | High | High | Info records, quotation comparisons and suitable outline agreements | Compare supplier price lists; investigate GRN rate changes against PO |
| Fraud and duplicate invoices | Medium | High | Configure duplicate invoice checks, authorizations and release strategy | Accounts cross-checks supplier invoice number, date and amount; owner reviews exceptions and audit log |
| Poor master data | High | High | Controlled material and supplier maintenance; validate units before planning | Named record owner checks descriptions, units and supplier price lists |
| Low user adoption | Medium | High | Role-based training with complete purchasing examples | Short practice sessions using PO, dispatch, GRN and payment scenarios |
| GST and e-way bill errors | Medium | High | Validate tax data and purchasing documents; accounts checks applicable requirements | Review invoice details, dispatch e-way bill and files; accountant verifies compliance |
| Missed MSME deadline | Medium | High | Correct payment terms, FI due-date review and F110 scheduling | Use MSME 45-day watch; accounts separately checks earlier applicable due dates |
| Single point of failure | Medium | High | Named substitutes, documented roles and tested recovery arrangements | Train a second operator; document access recovery and test available backup procedures |
| Damaged or unsuitable steel | High | High | Quality inspection stock, QM review and MIGO 122 return | Record damaged share, isolate on hold, raise debit note and track supplier credit |
| Supply or transport delay | High | High | Review open POs, delivery dates and MRP exceptions | Monitor supplier responses and partial dispatches; contact alternate suppliers early |
| Warnings routinely ignored | Medium | High | Assign ownership of invoice blocks and overdue reconciliation | Review Difference and Not checked cases daily; owner samples resolved cases |

I propose a short weekly exception meeting led by the buyer. Its agenda is limited to shortages, overdue commitments, damaged receipts, unresolved invoice differences and approaching payment deadlines. Each issue gets an action, an owner and a promised response date. Closed items retain their explanation, so repeated supplier problems remain visible.

Two practical safeguards make this more than a list. First, the team rehearses one combined failure: a key supplier delivers late, some steel is damaged and the invoice includes undelivered material. Stores, purchasing and accounts must agree their separate actions. Second, the owner checks a small sample of apparently clean transactions. A Matched label alone cannot detect a fictitious receipt or a wrongly selected material.

For compliance, attaching an e-way bill is not proof that it is correct or that every applicable requirement is met. Accounts remains responsible for the check. Similarly, an unresolved invoice dispute or a partial payment must not silently reset a supplier's due date. The payment plan must explicitly address the remaining balance.

## 8 Step-by-step strategy and timeline

This is a proposed 12-week organizational rollout, separate from the internship's six-week reporting schedule. The internship weeks describe feature development and study; the rollout includes preparation, pilot operation, training and review. I would use SAP as the process reference and choose one operational system for the workshop after confirming fit and cost.

| Phase | Weeks | Activities | Deliverable | Owner |
| --- | --- | --- | --- | --- |
| Establish scope | 1 | Confirm material groups, roles, records and goals | Agreed process scope and responsibility list | Owner and buyer |
| Prepare data | 2 | Check suppliers, units, specifications, stock and payment terms | Approved pilot data and baseline gaps | Buyer, stores and accounts |
| Plan supply | 3 | Review demand, lead times, critical materials and alternate sources | Buying plan and sourcing decisions | Production supervisor and buyer |
| Design controls | 4 | Define approvals, receipt checks, tolerances and exception ownership | Written control rules and practice cases | Owner and accounts |
| Pilot ordering | 5 | Trial selected materials and suppliers through order confirmation | Reviewed pilot POs and supplier responses | Buyer |
| Pilot receipt and match | 6 | Exercise partial dispatch, damage, invoice difference and return | Completed document chains and issue log | Stores and accounts |
| Improve pilot | 7 | Correct data and process issues; train substitute users | Pilot acceptance decision | Owner and process leads |
| Expand use | 8 | Add remaining priority materials and suppliers in batches | Wider purchasing coverage | Buyer and stores |
| Stabilize settlement | 9 | Review due dates, part payments, credits and SAP GR/IR where applicable | Reconciled open obligations | Accounts |
| Review performance | 10 | Calculate KPIs and assess supplier evidence | First consistent performance review | Buyer and owner |
| Test resilience | 11 | Rehearse absence, outage and alternate supply procedures | Recorded continuity drill and actions | Owner and backup operator |
| Accept and improve | 12 | Review targets, unresolved risks and recurring workload | Accepted operating procedure and next backlog | Owner with all process leads |

The pilot passes only when the team can trace an order through receipt, invoice review, payment and a return where relevant. Stores must explain stock differences, accounts must explain unpaid balances, and the buyer must explain open quantities. A screen demonstration alone is insufficient.

If an essential control fails, I would keep the pilot scope small and fix it before expanding. During cutover, opening stock, open POs and outstanding supplier dues need a dated reconciliation. The team must avoid entering old receipts again as new deliveries. There should be one agreed operational record for each transaction, with supporting paper retained where needed.

## 9 Resource allocation

The following hours are proposed allocations over 12 weeks, not historical effort or supplier quotations. They are time reserved within existing roles. Five primary users cover ownership, purchasing, stores, accounts and production; a substitute is trained for continuity.

| Person or role | Hours per week | Total hours | Main responsibility |
| --- | --- | --- | --- |
| Owner or manager | 2 | 24 | Decisions, exceptions and acceptance |
| Buyer | 6 | 72 | Data preparation, sourcing and supplier onboarding |
| Stores operator | 4 | 48 | Counts, receipts, damage and returns |
| Accounts employee | 4 | 48 | Invoice review, due dates and reconciliation |
| Production supervisor | 2 | 24 | Requirements, priorities and shortage review |
| Backup operator | 2 | 24 | Practice and continuity coverage |
| I, as Rigel builder and case coordinator | 3 | 36 | Feature explanation, pilot support and issue review |
| Total | 23 | 276 | Planned rollout effort |

Training should use short end-to-end examples during quieter periods. Receiving cover must remain available during training. If SAP implementation is chosen, specialist configuration and migration work requires a separate partner scope; the internal hours above do not substitute for that work.

**9.1 Budget in rupees**

I use only the costs in the supplied Rigel comparison note, dated 9 November 2026. Its SAP Business One figures are partner estimates, not an official price list. SAP Business One is a small-business cost comparator; its prices do not price the SAP MM transactions and integrated enterprise system described in this report.

| Cost item | SAP Business One style, five users | Rigel Growth |
| --- | --- | --- |
| Software | Rs 1,37,000 to Rs 1,60,000 per user perpetual, or about Rs 7,500 per user monthly cloud | Rs 24,000 yearly, up to 10 users |
| Annual support | 18% to 22% of licence value | Included |
| Setup and migration | Rs 5,00,000 to Rs 10,00,000 | Free until setup and migration finish, plus one month, capped at 90 days |
| Source's rough first-year headline | Rs 8,00,000 to Rs 12,00,000 | About Rs 24,000 |
| Source's indicative go-live time | 2 to 6 months | Days |

The note's headline SAP estimate does not reconcile with all its itemized perpetual costs. Five licences cost Rs 6,85,000 to Rs 8,00,000. Adding the stated support percentages and setup range gives a derived first-year range of Rs 13,08,300 to Rs 19,76,000. The cloud arithmetic is Rs 4,50,000 yearly for five users, plus setup, giving Rs 9,50,000 to Rs 14,50,000 before any separately quoted charges. These are calculations from the note, not new quotations.

For Rigel, I would provisionally reserve the stated Rs 24,000 annual subscription and existing staff time. Hardware, connectivity, taxes and any unquoted services remain to be confirmed; I have not invented amounts for them. The 12-week plan is a control rollout, so it can remain useful even when basic software access is available sooner.

**9.2 Technology needs**

The workshop needs reliable internet, usable computers or phones for the five roles, supplier email access and a way to retain invoice and delivery files. Named access, suitable permissions, a backup connection and tested recovery arrangements are rollout requirements. I would verify their availability rather than assume the subscription includes every item.

## 10 KPIs to track

I would establish one reporting period and consistent definitions before comparing suppliers. A percentage with no denominator is reported as not applicable. Quantities with different units are not added together. The locations below identify source records or reports; a calculated KPI may need a review worksheet rather than an existing dashboard tile.

| KPI | Formula | Target | SAP source or display | Rigel source or display |
| --- | --- | --- | --- | --- |
| On-time delivery | Lines due in period received by agreed date / all lines due x 100 | At least 95% | ME2N or ME2M plus receipt history; calculate | Supplier delivery report; reconcile due lines |
| Invoice mismatch rate | Checked GRNs with total difference above Rs 1 / checked GRNs x 100 | At most 5% | MIRO records and invoice review; calculate | GRN match results; calculate |
| Absolute price variance | Sum of received quantity x absolute rate difference / sum of received quantity x PO rate x 100 | At most 2% | PO conditions and receipt/invoice records; calculate | GRN rate comparison and price reports; calculate |
| Shortage stoppages | Count of production stoppages caused by missing material | At most one per four weeks | MD04 supports investigation; production log supplies count | Stock ledger supports investigation; production log supplies count |
| Damaged share | Damaged quantity / received quantity x 100, by comparable group and unit | At most 2% | QM findings and material documents; calculate | Quality report and GRN damaged quantities |
| Timely covered payments | Covered dues fully paid by applicable date / covered dues falling due x 100 | 100% | FI due-date records and payment history | MSME watch and GRN payments; accounts verifies dates |
| Match coverage | GRNs with invoice total checked / GRNs requiring invoice review x 100 | 100% before payment review closes | Invoice verification worklist and receipt reconciliation | GRN Matched, Difference and Not checked review |

Match coverage prevents a misleadingly low mismatch rate caused by leaving totals blank. Open overdue delivery lines remain in the on-time denominator. A later rescheduled date must not erase the original commitment without explanation. I would also review lead time and fill rate in Rigel's supplier delivery reports to understand why the headline delivery result changed.

## 11 Alignment with organizational objectives

The workshop's first objective is dependable customer delivery. Planned requirements, realistic supplier commitments and visible shortages help production sequence its work. The value is a clearer connection between customer promises and material availability, not simply more purchase orders processed.

The second objective is healthy job margins. Standard specifications, quotation comparisons and receipt rate checks expose changes before they become accepted routine. Measuring price alone would be misleading: damaged steel, urgent freight and lost production time can outweigh a small purchase discount.

The third objective is cash discipline. Buying to an agreed requirement limits unnecessary stock, while invoice checks prevent unexplained bills from becoming unquestioned payments. Part payments can support cash planning, but the remaining obligation and due date must stay visible. Paying covered suppliers on time also helps preserve future supply.

The fourth objective is a business that can operate when the owner or buyer is absent. Clear roles, a trained substitute and document history make decisions easier to understand later. Rigel's cancellation reasons and audit log support this objective; SAP provides broader structured controls when correctly implemented.

I would select the operational system according to these needs and the confirmed budget. Rigel offers a focused path for this small workshop. A larger organization needing deeper integration and planning may justify SAP. The process discipline should survive that choice, because reliable procurement depends on accurate records and accountable decisions in either system.

## 12 Conclusion and next steps

My procurement plan connects planning, sourcing, ordering, receiving, invoice verification and payment through a clear chain of responsibility. The hypothetical workshop gains a practical sequence of controls, measurable targets, risk responses and a 12-week implementation plan. None of the proposed results is presented as an achieved business outcome.

The Week 1 three-way match in Rigel makes two different problems visible: a supplier can bill more than arrived, and the receipt rate can exceed the PO rate. Its warning preserves receipt and part-payment flexibility while leaving the owner responsible for resolving the discrepancy. SAP MIRO provides a more formal, configurable invoice-control model alongside GR/IR accounting.

My next internship step is [Week 2: vendor evaluation and selection](../week-2/). I will use delivery reliability, fill rate, damage and price change to develop Rigel's supplier score and compare it with SAP vendor evaluation through ME61. Later weeks add damage reasons, approval above Rs 50,000 and buying suggestions. Together, these steps extend the same procurement discipline without claiming those features are already complete.

## Appendix: SAP MM transaction codes used

The table includes the related planning and FI transactions used in the procurement flow. They are not all owned by MM. Movement types identify goods movements within MIGO, not separate transaction codes.

| Code | Purpose in this plan |
| --- | --- |
| MM01 | Create material master |
| ME11 | Create purchasing info record |
| ME01 | Maintain source list |
| MD01 | Run material requirements planning |
| MD04 | Display stock and requirements list |
| ME51N | Create purchase requisition |
| ME41 | Create request for quotation |
| ME47 | Maintain supplier quotation |
| ME49 | Compare quotation prices |
| ME21N | Create purchase order |
| ME31K | Create purchasing contract |
| ME31L | Create scheduling agreement |
| MIGO | Post goods movements: 101 goods receipt; 122 return delivery |
| MIRO | Enter incoming invoice for logistics invoice verification |
| F110 | Run automatic payments in FI |
| ME61 | Maintain vendor evaluation |
| ME2M | Review purchasing documents by material |
| ME2N | Review purchasing documents by PO number |
| MB52 | Display warehouse stock |
| MB51 | Display material document list |
