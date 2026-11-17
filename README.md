<div align="center">

# Mohammad Alahmad

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Inter&weight=600&size=22&pause=1200&color=6366F1&center=true&vCenter=true&width=640&lines=strategy+%26+ops+main+character+%F0%9F%8E%AF;scaled+10+%E2%86%92+950%2B+locations%2C+no+cap;SQL+that+tells+managers+where+to+act;two+market+launches.+we+ate.)](https://linkedin.com/in/pemalahmad)

**Strategy & Operations lead who understood the assignment.**<br>
10 years across the GCC and EMEA: market research → engineering delivery → regional ops leadership.<br>
At Tesla I run strategy & ops for GCC and south EMEA: market entry, network scale-up, P&L and cost control, plus the data + AI layer the execs actually decide on. Lowkey the whole stack, highkey the results.

📍 Dubai, UAE · 🌐 Arabic (native) / English (fluent) · 🎓 B.Sc. Civil (Structural) Engineering · 📜 PMP

[![LinkedIn](https://img.shields.io/badge/LinkedIn-slide_in-0A66C2?logo=linkedin&logoColor=white)](https://linkedin.com/in/pemalahmad)
[![FleetOps](https://img.shields.io/badge/FleetOps-try_it_live-6366F1)](https://pemalahmad.github.io/FleetOps-KPI-Dashboard/)

![SQL](https://img.shields.io/badge/SQL-EDW-336791?logo=postgresql&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-E97627?logo=tableau&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)
![Apache Superset](https://img.shields.io/badge/Apache%20Superset-20A6C9?logo=apache&logoColor=white)
![Splunk](https://img.shields.io/badge/Splunk-000000?logo=splunk&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?logo=anthropic&logoColor=white)
![Power Automate](https://img.shields.io/badge/Power%20Automate-0066FF?logo=powerautomate&logoColor=white)
![SAP](https://img.shields.io/badge/SAP-0FAAFF?logo=sap&logoColor=white)
![Salesforce](https://img.shields.io/badge/Salesforce-00A1E0?logo=salesforce&logoColor=white)
![Jira](https://img.shields.io/badge/Jira-0052CC?logo=jira&logoColor=white)

</div>

---

## 🧾 The receipts

```text
┌──────────────────────────────────────────────────────────────────────┐
│  network scale            10  ──▶  950+ customer-facing locations    │
│  service productivity     ~30% uplift   (analytics-led turnarounds)  │
│  operating spend          ~20% lower  ·  up to $40M saved a year     │
│  regional P&L remit       ~$300M quarterly revenue                   │
│  market launches          2  ·  Saudi Arabia + Qatar, case → keys    │
│  peak org                 up to 3,500 people, via country managers   │
└──────────────────────────────────────────────────────────────────────┘
```

Not vibes. Numbers. Fr fr.

---

## 🚗 Currently cooking: [FleetOps KPI](https://github.com/Pemalahmad/FleetOps-KPI-Dashboard) · [try it live ▶](https://pemalahmad.github.io/FleetOps-KPI-Dashboard/)

Fleet software that's built different: every fleet KPI wired into **one network of equations**, built on my **Three Clocks Doctrine**. Exact identities (off-road hours = visits × hours per visit = workshop + pick-up + back to ops) plus measured drivers with standard errors, p-values and confidence intervals. The math is the main character; the dashboard is just the outfit.

- **Bring your own fleet:** drop an Excel VIN list (Fleetio / Samsara / Motive / Geotab / Verizon Connect exports get recognised), snap the registration cards, and get a fleet register with one next action per car. VINs validated + decoded, cards read in English *and* Arabic.
- **Runs in your browser:** a tested dbt-style SQL pipeline (59 models, 42 validation rules, 24 data tests) on DuckDB-WASM. Zero servers, zero uploads, your data stays yours.
- **Works offline:** install it as an app or download the package. Wi-Fi is optional, the vibes are not.
- **Receipts on the receipts:** what-if simulator, logistic regression, risk ratios, Welch tests. TypeScript / Next.js, plus a Python CLI.

[![FleetOps KPI metric network](https://raw.githubusercontent.com/Pemalahmad/FleetOps-KPI-Dashboard/main/docs/web-metric-network.jpg)](https://pemalahmad.github.io/FleetOps-KPI-Dashboard/network/)

---

## 🧠 Data, SQL & AI: the decision layer (it's giving one source of truth)

At Tesla I built the ops-analytics capability from scratch: an **enterprise data warehouse (EDW) on SQL**, the KPI models on top, and live dashboards that gave the C-suite **one source of truth** across 10 markets. Manual consolidation? Retired. Automated reporting? Locked in.

```mermaid
flowchart LR
    A["Operational data<br/>sales · delivery · service · charging · finance"] --> B[("EDW<br/>SQL data layer")]
    B --> C["KPI models<br/>cost · schedule · quality · risk<br/>throughput · budget vs actual"]
    C --> D["Live dashboards<br/>Tableau · Power BI · Superset"]
    C --> E["Monitoring<br/>Splunk"]
    C --> F["AI layer<br/>predictive analytics · automated reporting<br/>resource allocation"]
    D --> G["Executive cadence<br/>monthly summaries · quarterly scorecards<br/>C-suite reviews"]
    C --> H["Regulatory packs<br/>homologation · recall completion"]
    F --> G
```

| What I built | The glow-up it caused |
|---|---|
| **EDW / SQL data layer** across sales, delivery, service and charging | One source of truth for leadership; manual consolidation said bye |
| **KPI dashboards** (Tableau, Power BI, Apache Superset) on cost, schedule, quality and risk | Struggling markets and service centers got caught early, which drove the ~30% productivity turnarounds |
| **Monthly management summaries and quarterly scorecards** from the same layer | Exec reviews running on validated, consolidated data. No guessing |
| **Regulatory reporting packs** from the EDW | Evidence behind approval, homologation and recall-completion submissions to government authorities |
| **AI-driven KPI development, predictive analytics, automated reporting, resource allocation** | Risks spotted earlier, decisions made faster; every market opening became a repeatable playbook |
| **AI agents** for deep competitive and account research on new B2B leads | Every pitch built on the prospect's own market position. Unskippable |

<details>
<summary><b>How I write KPI SQL</b> (IYKYK): an illustrative pattern, synthetic schema, not employer code or data</summary>

```sql
-- Service-center turnaround & throughput: flag centers drifting from the regional baseline
WITH jobs AS (
    SELECT
        center_id,
        DATE_TRUNC('week', closed_at)                          AS wk,
        COUNT(*)                                               AS jobs_closed,
        AVG(EXTRACT(EPOCH FROM closed_at - opened_at) / 3600)  AS avg_turnaround_h
    FROM service_jobs
    WHERE closed_at >= DATE_TRUNC('week', CURRENT_DATE) - INTERVAL '12 weeks'
      AND closed_at <  DATE_TRUNC('week', CURRENT_DATE)   -- complete weeks only
    GROUP BY 1, 2
),
scored AS (
    SELECT
        j.*,
        ROUND(jobs_closed::numeric / NULLIF(c.technician_count, 0), 2) AS jobs_per_tech,
        AVG(avg_turnaround_h) OVER (PARTITION BY wk)           AS region_turnaround_h,
        AVG(jobs_closed) OVER (PARTITION BY center_id
             ORDER BY wk ROWS BETWEEN 3 PRECEDING AND 1 PRECEDING) AS trailing_4wk_jobs
    FROM jobs j
    JOIN service_centers c USING (center_id)
)
SELECT
    center_id, wk, jobs_closed, jobs_per_tech,
    ROUND(avg_turnaround_h, 1)                                 AS turnaround_h,
    ROUND(100.0 * (avg_turnaround_h / region_turnaround_h - 1), 1) AS pct_vs_region,
    CASE WHEN avg_turnaround_h > 1.2 * region_turnaround_h
           OR jobs_closed   < 0.8 * trailing_4wk_jobs
         THEN 'INTERVENE' ELSE 'OK' END                        AS status
FROM scored
ORDER BY wk DESC, pct_vs_region DESC;
```

Same pattern behind the turnaround work: baseline, drift, and an explicit intervention threshold. The dashboard doesn't just report, it tells a manager where to act this week. That's the whole point.
</details>

---

## 🏆 Main quests

### 1 · Network, service & leadership: Tesla
**Scaled the network to 950+ locations and lifted service productivity ~30%. Big W.**
- **Built repeatable operations.** Operating models, site playbooks and training frameworks, with staffing, parts, service workflows and escalation aligned to each market.
- **Made performance actionable.** Built the enterprise data warehouse (SQL/EDW) and live KPI dashboards (Tableau, Power BI, Apache Superset) that guided turnarounds of underperforming markets and service centers.
- **Developed leaders.** Hired, trained and led country and functional managers, connecting workforce plans, targets and resource allocation to regional priorities.
- **Turkey footprint:** 90,000-vehicle fleet · 6 stores · 9 service centers · 24 Supercharging stations.

### 2 · Market entry: Tesla Saudi Arabia & Qatar
**Launched two markets: 5,000 and 4,000 vehicles delivered in their opening quarters. We ate and left no crumbs.**

`Business case` → `Readiness` → `Mobilization` → `Delivery`

Market assessment and budgets; funding, hiring, policy and infrastructure coordination; site selection, workforce plans and launch playbooks; then sales, service, charging and vehicle-delivery ops. The regulatory side covered vehicle homologation, product approvals with engineering, policy and government teams, and consumer-finance programmes structured with central banks in four countries.

### 3 · Cost & operating control: Tesla regional P&L
**Cut operating spend ~20%, saving up to $40M a year. Budget said thank you.**
Owned regional, unit and departmental P&Ls: cost control, margin protection, cash flow, forecasting and budget-versus-actual. Led annual planning, target setting and resource allocation. Built the expansion business cases and ROI analysis, validated them with external consultancies, and took them from C-suite decision to implementation. Supported M&A with financial analysis, due-diligence input and post-deal integration.

## 🎮 Side quests (still S-tier)

### 4 · Programs & production: Creators HQ / 1 Billion Followers Summit
**Coordinated 50+ influencers across multi-set productions** (project-based, 2023 to present). Program frameworks, production SOPs, equipment-allocation plans and ClickUp task structures running creator shoots, summit production and live events end to end. Main character energy, but make it logistics.

### 5 · Engineering delivery: Stantec
**Led structural workstreams from concept to authority approval** as Engineer of Record on Abu Dhabi and UAE developments: an Abu Dhabi canal project, Saadiyat Island developments, and the Arada Central Business District at Aljada (40 office blocks, ~4.3M sq ft). Scope, budgets and milestones in Primavera; authority approvals with TAQA and Abu Dhabi Municipality.

### 6 · Design to fabrication: Gulf Precast
Built fabrication-ready TEKLA packages for a residential tower on Al Reem Island, and optimised reinforcement and mix designs to cut material use and production lead time. Efficiency era.

### 7 · Market research: Telecommunications Regulatory Authority (now TDRA)
**Led the market research behind the UAE entry of Virgin Mobile and Swyp,** from methodology and survey design to strategic entry recommendations. Benchmarked du and Etisalat against operator KPIs and turned survey and social-response analysis into a 40% CSAT improvement. Customers said slay.

---

## 📈 Eras

> From analysis to delivery. From delivery to regional leadership. Character development, fr.

| Era | Where | Unlocked |
|---|---|---|
| 2016 – 2018 | TRA (now TDRA) | Market & regulatory analysis |
| 2018 – 2019 | Gulf Precast | Design-to-production coordination |
| 2019 – 2021 | Stantec | Project controls & multidisciplinary delivery |
| 2021 – present | Tesla | Regional strategy, operations & P&L leadership |
| 2023 – present | Creators HQ / 1BFS (project-based) | Programs, partners & production operations |

---

## 🧰 Loadout

- **Strategy & finance:** business cases · financial modelling · ROI analysis · market entry · scorecards & OKRs · M&A support
- **Data & analytics:** SQL / EDW · data modelling for KPIs · Tableau · Power BI · Apache Superset · Splunk · forecasting · statistical analysis & survey design
- **AI & automation:** Claude Code · Claude · ChatGPT · Microsoft 365 Copilot · Gemini · Power Automate
- **Delivery:** PMO governance · Primavera P6 · MS Project · JIRA & Confluence · ClickUp · SAP · Salesforce

---

<div align="center">

📫 **Wanna build something that slaps? Slide into my DMs:** [linkedin.com/in/pemalahmad](https://linkedin.com/in/pemalahmad)

<sub>no NPC energy in this repo. touch grass, then ship.</sub>

</div>
