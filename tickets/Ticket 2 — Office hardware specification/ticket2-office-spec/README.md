
**Course:** IFT 103 — Operating System Architecture  
**Date of price check:** 2026-11-23  
**Budget:** 3,000,000 KZT  
**Proposed total:** 1,923,428 KZT  
**Remaining:** 1,076,572 KZT

## 1. What was asked

> We are opening the second office and need four computers — accountant, sales, web developer, designer. Budget 3,000,000 tenge for everything. Everyone says we should just buy the same four machines, is that right? Make sure they last a few years. Monitors included.

## 2. What was actually needed

Four identical computers are not the best solution because the four employees do different work. The accountant mainly needs reliable office and accounting software. The sales manager needs enough memory for a browser with many tabs, CRM and video calls. The web developer needs memory and CPU resources for an IDE, containers, databases and virtual machines. The designer needs a discrete GPU and a monitor suitable for visual work.

The request also leaves out several costs and decisions: licensed operating systems, keyboards, mice, cables, assembly, warranty, backup arrangements and whether the budget includes office software. I included the computer, one monitor and one licensed Windows installation per employee. I did not include keyboards, mice, UPS devices, backup drives, Microsoft Office subscriptions or assembly labour because the brief does not give their prices or say that they are required. The remaining budget should be used for these after the director confirms the priorities.

**Questions I would ask Daniyar:**
1. Which exact accounting, CRM, development and design applications will be used? Are there any applications that require Windows?
2. How many years should the computers remain under warranty, and is on-site support required?
3. Does the 3,000,000 KZT include keyboards, mice, UPS devices, backup storage, office software, assembly and VAT?
4. Does the designer work mainly with 2D graphics, video, CAD or 3D rendering? What colour accuracy and resolution are required?
5. Does the developer use Docker, WSL2 or several virtual machines simultaneously?

**Assumptions used:** I assumed a five-year useful life, standard 8-hour office days, Windows-compatible business applications, one Full HD monitor per person, and that keyboards/mice/UPS/office application subscriptions are outside this first estimate. I assumed the designer mainly does 2D design and light GPU-accelerated work, not professional 3D rendering. These assumptions must be confirmed before purchase.

## 3. What I did

I mapped each role to its workload, identified the likely bottleneck, and spent money on the part that matters most for that role. I did not use one identical configuration because the developer and designer need more memory and/or graphics capability than the accountant.

The four builds and their load/bottleneck/trade-off reasoning are in [builds.md](builds.md). The itemized dated price list is in [budget.csv](budget.csv).

**Budget result:** the proposed total is **1,923,428 KZT**, below the 3,000,000 KZT limit by **1,076,572 KZT**. The remaining amount is not treated as free spending; it is a reserve for price changes, input devices, UPS units, backup storage and assembly.

### Director question 1 — Which machine will be upgraded first in 18 months?

The sales manager's computer should be upgraded first. I would increase its memory from 16 GB to 32 GB because CRM, a large number of browser tabs, spreadsheets and video calls can use most of the available memory at the same time. When physical memory is exhausted, Windows uses the SSD as virtual memory, which is much slower and can make switching between applications feel unresponsive. The exact B760 board has four DIMM slots, so two additional matching 8 GB DDR4 modules could be added, subject to confirming the final board revision and memory compatibility.

### Director question 2 — What do pre-built computers cost, and what is gained or lost?

A local vendor's pre-built catalogue provides reference prices, not exact equivalents to the custom builds. For example, Technodom lists NEO Game A18 at 472,990 KZT (16 GB RAM, 512 GB SSD), NEO Game 89 at 492,990 KZT (16 GB RAM, 1 TB SSD, RTX 3050), NEO Game A10 at 635,990 KZT (32 GB RAM, 1 TB SSD, RTX 5060), and TechnoGaming 338 at 766,990 KZT (Core i5-13400F, RTX 5060, 32 GB RAM, 1 TB SSD). These are gaming-oriented machines, not exact role-matched office systems. The prices should therefore be treated as comparison examples, not as four direct quotations for the proposed builds.

**What the company gains:** one vendor is responsible for assembly and basic system testing; warranty handling is simpler; the company saves staff time; and support may be available from one supplier.

**What the company loses:** less control over the motherboard, PSU, cooling and memory configuration; potentially fewer upgrade choices; a discrete GPU may be included where it is not needed; and the price can be higher than a carefully selected parts list. The company should request four written role-matched quotations from an integrator before making the final purchase decision.

### Director question 3 — Who is most likely to complain within a month?

The sales manager is most likely to complain about slowdowns while switching between a large number of CRM tabs, spreadsheets and video calls. I selected 16 GB to protect the budget, but it is the weakest memory configuration relative to the employee's multitasking load. This is a deliberate compromise and the reason the sales machine is first in the upgrade plan.

## 4. Evidence

- [PCPartPicker compatibility notes](evidence/pcpartpicker-links.md) — explains what each list must verify. The actual saved share URLs still need to be created in PCPartPicker.
- [Vendor quote evidence folder](evidence/vendor-quotes/README.md) — checklist for the dated screenshots. Screenshots have not been fabricated; they must be captured from the live vendor pages before submission.
- [budget.csv](budget.csv) — itemized prices, vendors, source links and observation date.

## 5. What I would do differently

Before ordering, I would run a short workload test with the actual applications used by each employee and ask the designer for sample project files. I would also obtain written quotations from one business supplier for all four computers, monitors, Windows licences, assembly and warranty. This would make the comparison more reliable than relying only on catalogue prices. For the designer, I would test the monitor's colour coverage and calibration rather than assuming that every IPS display is suitable for professional colour work.

## Price and evidence limitations

The listed prices are a research snapshot dated 2026-11-23, not a guarantee that the seller will keep the same price. Some catalogue sources are category pages rather than stable product URLs. Before submission, open each exact item, confirm stock and the precise model, and replace any category link with its individual product page. Capture one screenshot per priced item with the vendor name, product/model, price and date visible. Also save four PCPartPicker lists and insert their real share URLs. Do not claim those screenshots or saved lists exist until they have actually been created.

## AI-use declaration

AI assistance was used to help draft and organize this report and budget. I will verify each component, compatibility decision, vendor price and evidence screenshot myself, and I will be able to explain the submitted choices.


> AI assistance was used to help draft and organize Ticket 2. I verified the final component choices, compatibility, prices and evidence before submission.
