# Vendor Evaluation and Selection in SAP MM: A Small Indian Steel Workshop and Rigel ERP

Pawan Singh Kapkoti

YuvaIntern SAP MM Procurement Specialist, Week 2

November 2026

## 1 Executive summary

A supplier's lowest quotation is useful only if the right material arrives in time and in usable condition. In Week 1, I connected procurement planning, purchase orders, receipts, invoice checks and payment. This report follows the next step promised in that report: using delivery reliability, fill rate, damage and price change to evaluate suppliers and guide future buying.

The case remains a hypothetical Indian steel fabrication workshop with about 25 people, annual turnover of about Rs 6 crore and approximately 30 suppliers. It buys steel sections, plates, fasteners and paint. The company, supplier examples and proposed results contain no real customer data. I use SAP MM as the process reference and compare it with Rigel ERP, which I build for small Indian traders and workshops.

The Week 2 feature is Rigel's supplier score, live on Reports > Purchase > Suppliers. It gives on-time delivery 40 points, fill rate 30, damage 20 and price 10. It uses existing purchase orders and goods receipt notes, or GRNs. Missing parts are excluded from the available weight, and fewer than two parts with data means no score is shown. The owner sees the lowest scores first and decides what action to take.

I propose a selection process, monthly supplier reviews and a focused rollout over 4 to 6 weeks. The report includes a scoring matrix, worked examples, SAP comparisons, risks, staff effort, a planning budget and KPIs. Targets and costs are assumptions to review, not achieved improvements or supplier quotations.

## 2 Why vendor evaluation matters for the workshop

The workshop needs steel before cutting, drilling and welding can begin. A late load can hold several people and leave a partly completed job occupying space. Buying from an emergency source may restore production, but urgent freight and a higher rate can remove the saving from the original order. I would judge delivery reliability alongside price because these consequences reach beyond the purchase register.

Short supply creates a different problem. A truck may arrive on the promised date with only part of the requirement. Stores records a receipt, yet production still lacks enough material to complete the job. A supplier who delivers small quantities promptly should not appear dependable simply because every arrival was on time. This is why the matrix measures both timing and quantity.

Rust, bent sections and the wrong size reduce usable stock. A plate of the wrong thickness cannot be treated as interchangeable merely because its weight is correct. Fasteners with the wrong dimensions can stop assembly, while unsuitable paint can cause rework. Stores needs a consistent receipt check and a record of the affected quantity. Production must also report defects found after receipt.

Price creep is less visible. A supplier quotes one rate, accepts the PO and then supplies at a higher rate. A small increase repeated across purchases can reduce the job margin. Week 1's GRN rate comparison exposes the individual difference. Week 2's score helps show whether that behavior repeats across the supplier relationship.

I assume the current buying decision depends partly on memory and personal familiarity. Those relationships can help resolve shortages, but memory gives extra attention to the most recent incident. A documented review gives the owner evidence for a supplier conversation and a reason for allocating future orders. It also shows where the workshop itself contributed to a problem through unclear specifications, late ordering or delayed payment.

## 3 Vendor evaluation in SAP MM

I use the classic SAP MM vendor evaluation process for this report. Its standard scoring range is 1 to 100, with higher scores indicating better performance. Purchasing and receipt information can feed evaluation, and QM supplies quality evidence. Main criteria include price, quality, delivery and general service/support. SAP also supports other criteria and external service evaluation. The exact functions available depend on the installed system and configuration. These principles follow [SAP's MM vendor evaluation overview](https://help.sap.com/docs/SAP_ERP/3e0f68e22536463481065831d476a767/ace1b853dcfcb44ce10000000a174cb4.html).

**3.1 Prepare the purchasing sources**

ME11 creates a purchasing info record for a material and supplier relationship. It can hold prices, conditions and supply information. For the workshop, the buyer should maintain the correct steel specification, order unit and agreed commercial basis before relying on price comparisons. An info record supplies purchasing information; its existence alone does not prove that the supplier has passed a quality trial. This use follows [SAP's info record documentation](https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/8a57feade137489098f59374c06f1e0e/6e07b753128eb44ce10000000a174cb4.html).

ME01 maintains the source list for a material and plant over defined validity periods. Source entries can identify permitted sources, a fixed source or a blocked source, according to the relevant settings. I would use it to support the workshop's approved sourcing decisions. The approval evidence, such as sample checks and owner authorization, still needs to be retained. SAP explains these controls in its [source list guidance](https://learning.sap.com/courses/purchasing-in-sap-s-4hana/controlling-source-determination-with-source-lists-1).

MEQ1 maintains quota arrangements. A quota specifies a source's share of a material requirement over a period and influences source assignment where the arrangement is used. I would consider it after qualifying an alternate steel supplier. It is not a rule that every PO must be divided into the same percentages, and a vendor score does not itself rewrite a quota. This distinction follows [SAP's quota arrangement documentation](https://help.sap.com/docs/SAP_ERP_SPV/6cfdc7caaef746cd9c7543e32e7e87c0/f006b753128eb44ce10000000a174cb4.html).

**3.2 Main criteria and supporting evidence**

Main criteria are broken into subcriteria so that a weak result can be traced to its cause. I would begin with the following evidence and keep manual judgments documented.

| Main criterion | Relevant subcriteria or checks | Evidence and meaning for this workshop |
| --- | --- | --- |
| Price | Price level and price history | Purchasing prices and conditions, including PO history and info records, support comparison with the relevant market price basis |
| Quality | Goods receipt quality and complaints/rejection level | QM inspection results or quality notifications identify defects and their consequences |
| Delivery | On-time delivery performance and quantity reliability | PO commitments and goods receipts show date and quantity performance |
| Service | General service/support, including response to problems | Buyer records support a manual or semi-automatic assessment where configured |

SAP's price level compares the supplier's effective price with a market price basis. Price history considers how the supplier's prices changed relative to market price changes. These are broader assessments than checking whether one GRN rate exceeded its PO rate. The workshop must maintain useful purchasing prices and a defensible comparison basis. I would not describe Rigel's price part as a copy of either SAP calculation. See SAP's explanations of [price level](https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/af9ef57f504840d2b81be8667206d485/f7e4b953495bb44ce10000000a174cb4.html?source=productlink-webassistant) and [price history](https://help.sap.com/docs/PRODUCT_ID/b704a8db767040a08100adc846218964/fae4b953495bb44ce10000000a174cb4.html?locale=en-US&state=PRODUCTION&version=6.06.34).

On-time delivery and quantity reliability should be read together. Quality evidence can include an incoming inspection and a later complaint from production. Service requires care because a friendly telephone response is not proof that a replacement arrived. SAP distinguishes automatic, semi-automatic and manual subcriteria; I would select methods according to the evidence the workshop can maintain. These distinctions follow [SAP's subcriteria documentation](https://help.sap.com/docs/SAP_ERP/b704a8db767040a08100adc846218964/ce77b6535fe6b74ce10000000a174cb4.html?version=6.18.latest).

**3.3 Setup, weighting and maintenance**

Before evaluation, the SAP configuration must define the relevant criteria, scoring settings and purchasing organization parameters. A weighting key groups the weights assigned to main criteria. Equal weighting gives each criterion the same influence; unequal weighting gives more influence to selected criteria. I would favor delivery and quality for production-critical steel, then review that choice with the owner. SAP describes this mechanism in [Weighting of Scores](https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/af9ef57f504840d2b81be8667206d485/d477b6535fe6b74ce10000000a174cb4.html).

ME61 maintains vendor evaluation. ME63 performs automatic new evaluation, recalculating the relevant automatic subcriteria. ME64 compares evaluations, and ME65 provides ranking lists. These transactions support review; they do not replace configuration or the buyer's sourcing decision. Their purposes are documented under [evaluation maintenance](https://help.sap.com/docs/SAP_ERP/6cfdc7caaef746cd9c7543e32e7e87c0/7707b753128eb44ce10000000a174cb4.html?version=6.18.latest) and [evaluation lists](https://help.sap.com/docs/SAP_ERP/666b7ae6edfe4c05a90ac0150637f964/9507b753128eb44ce10000000a174cb4.html).

Automatic updating needs a precise explanation. Goods receipts and QM events can update evaluation statistics, while the saved evaluation still shows its earlier scores until re-evaluation. I would therefore include re-evaluation in the monthly routine and check the evaluation date before comparing suppliers. SAP explains this separation in its [automatic scoring overview](https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/af9ef57f504840d2b81be8667206d485/3478b6535fe6b74ce10000000a174cb4.html).

**3.4 Approval and blocking**

The proposed approved vendor list records the material scope, trial result, approving person and review date. Approval for fasteners does not establish competence to supply structural steel. I would maintain this decision record alongside the relevant SAP sourcing records.

XK05 is the classic transaction for blocking a vendor centrally. Purchasing and posting blocks have different purposes, so the responsible user must select the intended scope. In S/4HANA, the legacy blocking transaction can redirect to business partner maintenance. A poor evaluation requires a separate decision about restrictions and open documents. SAP's [blocking guidance](https://learning.sap.com/courses/purchasing-in-sap-s-4hana/blocking-sources-of-supply) explains these distinctions. I would never assume that a low score automatically blocks purchasing or cancels existing obligations.

## 4 Designing the scoring matrix for the workshop

I use four measurable criteria because the workshop already records the documents needed for them. The weights total 100. Delivery timing and fill rate together receive 70 because missing material directly interrupts fabrication. Damage receives 20 because received goods may still be unusable. Price receives 10 to expose changes against agreed rates without letting a cheap quotation outweigh repeated supply failures.

| Criterion | Weight | How it is measured | Data source | Why this weight |
| --- | --- | --- | --- | --- |
| On-time delivery | 40 | Share of GRNs received by the PO's expected date | PO expected date and GRN receipt date | Late steel can stop several production activities |
| Fill rate | 30 | Average over PO lines of the share of each line received, each line capped at 100% | PO line quantities and their received quantities | A prompt but short delivery can still leave a job unfinished |
| Damage | 20 | Damaged quantity as a share of received goods; points fall to zero at 10% damage | Received and damaged quantities on GRN lines | Protect usable stock and expose handling or supply problems |
| Price | 10 | Extra paid above the PO rate as a share of the received goods' value at the PO rate; points fall to zero at a 10% rise | PO rates, supplier rates on the GRN and received quantities | Discourage unexplained changes to agreed buying cost |
| Total | 100 | Available parts are combined under the rules in section 5 | Existing purchasing and receipt documents | Keep the calculation explainable to a small team |

These weights are the fixed rules of this week's Rigel feature. The matrix is not an assertion that SAP uses the same weights or formulas. Service remains part of the workshop's review notes, including response to shortages, replacement speed and cooperation on credits. It does not receive an extra weight in Rigel's score.

Before using the matrix, I would reconcile the selected documents and identify missing dates, quantities or rates. A blank damage record is different from an inspected receipt with zero damage. Quantities in kilograms, pieces and litres must not be added as if they were interchangeable. The buyer should inspect comparable material and unit evidence when interpreting a supplier total. This is a review requirement, not a claim about an additional Rigel conversion feature.

The weights express priorities, but they do not define material acceptance. A supplier can have a strong total and still deliver an unsuitable plate. Stores and production must reject or isolate unsuitable material according to the receipt procedure. The score informs future allocation; the physical and specification checks decide whether a particular receipt can be used.

## 5 Rigel's supplier score

The supplier score built this week is live on Reports > Purchase > Suppliers. It uses the purchase orders and GRNs already in Rigel, including received and damaged quantities per line and the supplier's rates on the GRN. The owner can use the result alongside Week 1's invoice and rate checks. No separate supplier questionnaire is required for these four parts.

**5.1 Exact calculation rules**

On time measures the share of GRNs received by the PO's expected date. A share from 0 to 100% earns the same share of 40 points. For example, 90% on time earns 36. This counts GRNs for the timing measure. It is different from Week 1's proposed KPI based on all delivery lines due, so the two percentages should not be presented as interchangeable.

Fill rate is the average, over the supplier's PO lines, of how much of each line has been received, each line capped at 100%. A share from 0 to 100% earns the same share of 30 points. Averaging by line means a short line of bolts counts as much as a short line of plates, whatever their units. A 95% fill rate earns 28.5. The part does not award extra points above full receipt. Receiving goods and finding them usable are separate questions; the damage part records the latter problem rather than silently changing the fill definition.

Damage measures the share of received goods marked damaged on the GRN. Zero damage earns all 20 points. Damage of 10% or more earns zero. Between those limits the points fall in a straight line, so 5% damage earns 10 points and 2% earns 16. The measure depends on stores recording the damaged quantity consistently.

Price measures how much more was paid than the PO rates, as a share of what the received goods would have cost at those rates: the sum of (GRN rate minus PO rate) x quantity received, divided by the sum of PO rate x quantity received. No rise, or a fall, earns all 10 points. A rise of 10% or more earns zero, with a straight line between. A 3% rise earns 7 points. Working in value means a small receipt carries less influence than a large one, and a rise on cheap fasteners cannot outweigh the steel bought at the agreed rate.

| Part | Points rule when data is available | Maximum |
| --- | --- | --- |
| On time | On-time percentage / 100 x 40 | 40 |
| Fill rate | Fill percentage / 100 x 30, within 0 to 100% | 30 |
| Damage | 20 x (1 minus damage percentage / 10), bounded between 0 and 20 | 20 |
| Price | 10 x (1 minus value-weighted price rise percentage / 10), bounded between 0 and 10 | 10 |

In this table, a percentage is entered as its percentage number: 2 means 2%, not 0.02. No reduction is made below the maximum price points when the weighted rate change is zero or negative. A fall does not earn more than 10 points. Both penalty parts stop at zero, so severe damage or price rises cannot create negative points.

**5.2 Missing data, rounding and grades**

A part with no data is left out. Its weight is also left out of the denominator. The final calculation is score = points earned / weight available x 100, rounded. I retain the component points when explaining the calculation and round the final score. Fewer than two parts with data means no score is shown.

The grade is A for 80 and above, B for 60 to 79, and C below 60. The list shows the lowest scores first so the owner sees which suppliers need a talk. The result is shown only: it blocks no supplier and changes no PO. The owner decides whether to request improvement, change future buying or continue with a documented explanation.

Missing information is not proof of good performance. A score based on two parts answers a narrower question than a score based on all four. I would record the available parts and document count in the review notes, without claiming that these notes or counts are additional fields already built into the report screen.

**5.3 Worked supplier examples**

The following suppliers and measurements are hypothetical examples. They demonstrate the fixed calculation and do not represent actual customer records.

| Supplier | On time | Fill | Damage | Price rise | Points earned | Available weight | Score | Grade |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Supplier A: Shree Steels | 90% | 95% | 2% | 3% | 36 + 28.5 + 16 + 7 = 87.5 | 100 | 88 | A |
| Supplier B: Om Fasteners | 60% | 80% | 8% | 6% | 24 + 24 + 4 + 4 = 56 | 100 | 56 | C |
| Supplier C: Ganga Paints, new | 70% | 90% | No data yet | No data yet | 28 + 27 = 55 | 70 | 79 | B |

Shree Steels earns 87.5 points out of 100, rounded to 88, grade A. Its strong total supports consideration for more volume, but the buyer should still discuss the 2% damage and 3% price rise. An A grade does not mean that every delivery was correct.

Om Fasteners earns 56, grade C. Its shortages and timing already reduce the result, while damage and price increases leave only four points in each of those parts. I would review the underlying receipts before agreeing corrective action. Changing suppliers without checking the required fastener specification and alternate capacity could create another shortage.

Ganga Paints has only timing and fill data. Its 55 points are taken over 70 available, giving 79 after rounding, grade B. The absent damage and price parts are not scored as zero and are not awarded full marks. As evidence becomes available, the score will cover more of the supplier's performance. The examples therefore require different levels of confidence even though each has a grade.

## 6 SAP MM vendor evaluation compared with Rigel's score

Both approaches use purchasing evidence to support supplier decisions. Their scope differs. SAP provides configurable criteria, QM integration and evaluation processes across a larger purchasing structure. Rigel uses four parts that a small workshop can explain from documents it already enters. I would choose according to operational needs and the effort the team can sustain.

| Comparison | SAP MM vendor evaluation | Rigel supplier score |
| --- | --- | --- |
| Criteria | Price, quality, delivery, service and other configured criteria, with subcriteria | On time, fill rate, damage and price change |
| Weighting | Weighting keys and configured factors permit equal or unequal emphasis | Fixed weights of 40, 30, 20 and 10; missing parts excluded |
| Data source | PO and purchasing information, goods receipts, QM results and maintained assessments | POs, GRN quantities, damage quantities and supplier receipt rates |
| Automatic or manual | Automatic statistical updates, re-evaluation, and manual or semi-automatic methods as applicable | Calculation from available document data; owner interprets the result |
| What happens with the result | Supports sourcing review; restrictions and quota changes require the relevant separate controls | Lowest scores shown first; no supplier block or PO change |
| Cost and effort | Configuration, data preparation, specialist support and ongoing maintenance according to scope | Simpler document preparation and a small team's review routine; budget assumptions in section 10 |

The SAP capabilities in this comparison follow its [vendor evaluation overview](https://help.sap.com/docs/SAP_ERP/3e0f68e22536463481065831d476a767/ace1b853dcfcb44ce10000000a174cb4.html) and [automatic update guidance](https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/af9ef57f504840d2b81be8667206d485/3478b6535fe6b74ce10000000a174cb4.html). They should not be reduced to a claim that SAP requires manual scoring for every receipt or that a saved evaluation is always current.

SAP's quality assessment can use more evidence than a damaged quantity. A defect found during production may generate a QM notification even when the receipt appeared sound. SAP's price assessment can also consider market context. Rigel's score is narrower: it summarizes recorded receipt performance and changes against the PO rate.

For a 25-person workshop, fewer inputs can make regular review easier. The limitation is that the owner must separately consider service, hidden defects, market prices and supplier capacity. A larger business needing these assessments across many materials and organizational units may justify SAP's additional setup. Neither system makes poor records dependable merely by displaying a numerical result.

## 7 Vendor selection process for a new supplier

I would qualify a new supplier against a defined requirement before considering regular volume. The buyer first confirms the material specification, unit, required quantity, delivery location and acceptable lead time with production. For steel, the enquiry must distinguish grade, size and thickness. A general request for the cheapest available steel would produce quotations that cannot be fairly compared.

In SAP, ME41 creates the request for quotation, ME47 maintains the supplier quotation and ME49 provides quotation price comparison. These functions record the commercial offers; the buyer still checks technical suitability and total buying terms. Their purposes follow SAP's [RFQ documentation](https://help.sap.com/docs/SAP_ERP/6cfdc7caaef746cd9c7543e32e7e87c0/c306b753128eb44ce10000000a174cb4.html) and [quotation documentation](https://help.sap.com/docs/SAP_ERP_SPV/666b7ae6edfe4c05a90ac0150637f964/9306b753128eb44ce10000000a174cb4.html).

| Stage | Workshop action | Evidence before proceeding |
| --- | --- | --- |
| Enquiry | Obtain comparable quotations from suitable candidates | Common specification, quantity, required date and quotation validity |
| Commercial comparison | Compare rate, freight, taxes, delivery commitment and payment terms | Dated comparison with differences explained |
| Identity and registration | Check supplier identity, GSTIN and claimed MSME registration | Verified details and accounts review |
| Sample assessment | Inspect samples or a representative material quantity | Stores and production record dimensions, condition and suitability |
| Trial order | Place a limited order with clear acceptance conditions | Owner approval and supplier commitment |
| First three GRNs | Review timing, fill, damage, rates and response to problems | Receipt evidence, available score parts and open issues |
| Selection | Approve, extend the trial or reject the source | Owner's decision, material scope and next review date |

Accounts should verify the GSTIN and business identity through the [GST taxpayer search](https://tutorial.gst.gov.in/userguide/taxpayersdashboard/Search_Taxpayer_manual.htm), and check a claimed Udyam registration through the [official verification service](https://www.udyamregistration.gov.in/Udyam_Verify.aspx). The review should establish the supplier's relevant enterprise category and payment treatment. A registration check does not establish the quality of a steel load, and a sample does not verify registration. Both checks serve separate purposes.

The first three GRNs provide an initial review point, not proof of long-term reliability. I would check whether they represent separate meaningful deliveries or small receipts against one load. This review rule does not change Rigel's minimum of two parts with data for displaying a score. A new supplier can have a score while remaining on trial.

After approval, performance helps set future allocation. For example, I might propose 70% of a critical material's planned volume for a proven source and 30% for a qualified alternate, subject to capacity and price. SAP can represent the approved sourcing decision through source lists and quota arrangements. In Rigel, the buyer makes the allocation decision and issues the POs. No automatic score-to-quota function is claimed. A high score for paint would not qualify that supplier for steel.

## 8 Supplier development and review cadence

I propose a monthly score review led by the buyer and attended by the owner, stores and accounts. Production joins for shortages or quality problems. The buyer prepares the lowest scores first, checks the underlying documents and brings unresolved actions from the previous month. Critical shortages or unsuitable material require attention when discovered; the monthly meeting is for recurring performance and sourcing decisions.

Every C supplier gets a talk based on specific receipts. For Om Fasteners, I would separate late delivery, short supply, damage and rate differences, then ask for a practical correction to each repeated issue. The action record names the problem, responsible person, promised date and evidence needed to close it. A promise to improve is not the same as a corrected delivery.

Supplier development should address causes the supplier can change. Better packing may reduce damage, an earlier dispatch confirmation may reveal a likely delay, and a written rate confirmation may prevent disagreement at receipt. The workshop must also correct its own errors. Sending an order late or changing the specification after confirmation makes a supplier improvement discussion incomplete.

Consistent A suppliers should be considered for more volume and faster payment where cash planning permits. These are owner decisions based on capacity, price and continued acceptance of the material. I would keep a qualified alternate for critical steel even when the main supplier performs well. Repeated C results, unresolved serious defects, capacity limits or dependence on one source are reasons to look for a second source before an emergency.

Payment fairness applies to every grade. For covered micro and small suppliers, a written payment agreement cannot extend beyond 45 days from acceptance or deemed acceptance; without such an agreement, the relevant period is 15 days. An agreed earlier deadline still matters. These limits follow the [public MSME guidance](https://odr.msme.gov.in/assets/pdf/MSE_Scheme_on_ODR_for_Delayed_Payment_Guidelines.pdf). Accounts should confirm coverage and the applicable date, rather than treating every supplier as having a universal 45-day term.

A C grade is not a reason to delay an otherwise payable amount. Faster payment for an A supplier should mean earlier than its applicable deadline, not that other suppliers are paid late. This keeps the review fair and protects the supply relationship the workshop is trying to improve.

## 9 Risks of scoring and how to handle them

A score compresses several events into one number. That makes comparison easier but can hide differences in evidence, material importance and responsibility. I would keep the calculation unchanged and record context separately. Correcting a genuine data error is appropriate; editing a valid date or damage entry to improve a grade is not.

| Risk | How it can mislead | Mitigation and responsibility |
| --- | --- | --- |
| Small sample sizes | A new supplier's two good receipts appear as convincing as months of history | Buyer records document count and available parts; owner retains trial status until evidence is sufficient |
| A single late load | One exceptional incident changes the grade sharply | Review the incident, previous pattern and recovery; preserve the recorded score |
| Buyer's own late PO | Supplier is blamed for a date it could not reasonably meet | Buyer retains order issue date and commitment evidence; owner assigns internal corrective action |
| Market-caused price rises | A price penalty is treated as proof of unfair dealing | Compare dated quotations and market evidence; discuss approved changes separately without rewriting the formula |
| Gaming | Split receipts, shifted expected dates or omitted damage improve results | Owner samples PO changes, delivery evidence and physical checks; stores records actual receipts |
| Missing data | A partial score is read as a complete assessment | Review missing parts explicitly; never replace unavailable damage with zero damage |
| Mixed materials or units | Large quantities of small items hide failure on critical steel | Review comparable groups and units; production flags critical material failures |
| Defects found later | Clean receipt records hide faults discovered during fabrication | Production reports defects; buyer retains the quality evidence alongside the score |

The proposed review should also protect suppliers from inconsistent treatment. The buyer should give them the relevant PO and GRN references, record their explanation and correct supported mistakes through the normal document process. The owner decides whether the explanation changes future allocation. It does not justify silently replacing an inconvenient score.

A second check is useful even for high performers. I would sample one A supplier's receipt chain each month as well as reviewing every C supplier. This can uncover unrecorded damage or missing comparisons that a favorable total would otherwise hide. The procedure checks the evidence without adding new weights or changing the displayed grade rules.

## 10 Implementation timeline and resources

I propose 4 to 6 weeks to establish this supplier review process within the broader 12-week rollout described in Week 1. These are operational rollout weeks, separate from the internship calendar. The supplier score is already this week's feature; the timeline covers data preparation, practice, supplier review and acceptance of the working procedure.

| Phase | Rollout week | Work | Deliverable and owner |
| --- | --- | --- | --- |
| Define the pilot | 1 | Select frequent suppliers and critical materials; agree review responsibilities | Pilot scope and evidence checklist, buyer and owner |
| Prepare evidence | 2 | Reconcile PO links, expected dates, quantities, rates and damage records | Checked records and missing-data list, buyer and stores |
| Practice the review | 3 | Recalculate examples; rehearse supplier discussions and selection decisions | Review notes and trained substitute, process leads |
| Run the first cycle | 4 | Review scores, discuss C suppliers and approve corrective actions | Dated decisions and action owners, owner |
| Extend coverage | 5, if needed | Add remaining active suppliers and review trial receipts | Wider coverage and updated source decisions, buyer |
| Confirm routine | 6, if needed | Check actions, payment fairness and recurring workload | Accepted monthly procedure, owner and accounts |

A four-week pilot is reasonable if the records are usable and enough receipts exist. Sparse deliveries or unresolved data gaps justify weeks 5 and 6. The team should not manufacture receipt evidence to meet the timetable. Completion means that it can trace each reviewed score to documents and explain the resulting buying decision.

**10.1 People and planned hours**

| Person or role | Total hours over the rollout | Main work |
| --- | --- | --- |
| Owner or manager | 8 | Approve scope, actions and sourcing changes |
| Buyer | 24 | Prepare evidence, comparisons and supplier reviews |
| Stores operator | 16 | Check receipt quantities, dates and damage recording |
| Accounts employee | 10 | Check rates, registration evidence and payment dates |
| Production supervisor | 8 | Confirm material suitability and shortage consequences |
| Backup operator | 6 | Practice receipt checking and review preparation |
| I, as Rigel builder and case coordinator | 12 | Explain calculation, support practice and review issues |
| Total | 84 | Planned internal effort |

The allocation averages 14 person-hours per week over six weeks, spread across existing roles. It is a planning allowance, not a record of hours worked. Receiving and production need cover during practice. Any SAP configuration or implementation project would require a separate specialist scope.

**10.2 Planning budget in rupees**

| Item | Assumption | Amount |
| --- | --- | --- |
| Internal time | 84 hours at an assumed blended value of Rs 300 per hour | Rs 25,200 |
| Sample checks and local transport | Extra trial-related allowance, excluding normal material purchases | Rs 4,000 |
| Training materials | Small allowance for practice and checklists | Rs 1,000 |
| Contingency | Reserve for additional checking or a repeat visit | Rs 3,000 |
| Incremental rollout total | Internal effort plus the three allowances | Rs 33,200 |
| Rigel annual provision, if not already budgeted | Carry forward Week 1's case assumption | Rs 24,000 |
| Total including that annual provision | Avoid counting the subscription twice | Rs 57,200 |

All amounts are hypothetical planning provisions. The internal time value is not an extra salary bill. The Rs 24,000 subscription figure carries forward Week 1's supplied comparison note; it is not a newly verified quotation. Hardware, taxes and unquoted services require confirmation. I do not use Week 1's SAP Business One estimate to price an SAP MM implementation. The workshop can begin with existing devices, document access and a named substitute once these are checked.

## 11 KPIs to watch

I would establish the baseline during the pilot, then review the same definitions monthly. Targets below are proposed management goals, not results already achieved. The score summarizes receipt evidence, while the operating KPIs check whether material availability, data quality and follow-up are improving.

| KPI | Definition or calculation | Proposed target | Owner |
| --- | --- | --- | --- |
| Receipt on-time share | GRNs received by PO expected date / GRNs with comparable date evidence x 100 | At least 95% | Buyer |
| Fill rate | Average over PO lines of received / ordered x 100, each line capped at 100% | At least 95% | Buyer and stores |
| Damaged share | Damaged quantity / received quantity x 100, by comparable group and unit | No greater than 2% | Stores |
| Weighted price rise | Extra paid above PO rates / value of received goods at PO rates x 100 | No unexplained positive rise | Buyer and accounts |
| Scoring coverage | Active suppliers with enough data for a score / active suppliers reviewed x 100 | Every missing case has an owner and reason | Buyer |
| C supplier follow-up | C suppliers discussed in the cycle / C suppliers identified x 100 | 100% | Owner |
| Action closure | Actions closed by promised date / actions due x 100 | At least 90% | Buyer |
| Second-source coverage | Critical materials with a qualified alternate / critical materials reviewed x 100 | 100% | Buyer and production |
| Timely covered payments | Covered dues fully paid by applicable date / covered dues falling due x 100 | 100% | Accounts |

A percentage with no valid denominator is unavailable, not zero. The receipt timing measure does not expose an order for which nothing has arrived, so I would also review overdue open quantities. Week 1's due-line KPI remains useful for that broader view. Changing the mix of receipts can change the score without resolving an old shortage.

These calculations and action measures may need a review worksheet; I do not claim they are all existing Rigel dashboard fields. The monthly review should retain its period, document references and decisions. That makes a change in grade explainable and helps separate improved supply from improved data coverage.

## 12 Conclusion and next steps

Vendor evaluation gives the workshop a repeatable way to connect supplier behavior with future buying. SAP MM provides purchasing source records, configurable criteria, weighted evaluation and links to receipt and QM evidence. Rigel's score applies four fixed measures to documents the workshop already uses. The comparison shows how the same purchasing discipline can operate at different levels of detail.

The worked examples show why the total needs explanation. Shree Steels scores 88, grade A, while Om Fasteners scores 56, grade C. Ganga Paints scores 79, grade B, using only 70 available weight because damage and price data are absent. None of these results automatically changes a PO or blocks a supplier. The owner remains responsible for qualification, corrective action, allocation and fair payment.

My next internship step is [Week 3: master data management](../week-3/). I will focus on consistent material descriptions, units and supplier records, and add the damage reason on a GRN line. That reason should help distinguish issues such as broken goods, wrong size, rust and short weight when reviewing suppliers. The Week 2 feature measures the damaged share; the planned Week 3 work adds the explanation needed for better follow-up. These next steps continue the document-based procurement approach established in Week 1.

## Appendix: SAP MM transaction codes used

The table lists the transactions discussed in this report. XK05 is a central vendor maintenance transaction; its use in S/4HANA can redirect to business partner maintenance. Availability and authorization depend on the installed system.

| Code | Purpose in this report |
| --- | --- |
| ME11 | Create purchasing info record |
| ME01 | Maintain source list |
| MEQ1 | Maintain quota arrangement |
| ME61 | Maintain vendor evaluation |
| ME63 | Automatic new evaluation of the relevant automatic subcriteria |
| ME64 | Compare vendor evaluations |
| ME65 | Display vendor ranking lists |
| XK05 | Block or unblock vendor centrally |
| ME41 | Create request for quotation |
| ME47 | Maintain supplier quotation |
| ME49 | Compare quotation prices |
