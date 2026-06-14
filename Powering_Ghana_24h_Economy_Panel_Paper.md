# Powering Ghana’s 24‑Hour Economy — Practical Pathways for Transport Infrastructure and Energy Mobility

**Author:** Rev. Engr. Dr. Frimpong Kyeremeh

**Event:** Ghana Investment & Trade Week (GITW) 2026 — Panel: Transport Infrastructure & Energy Mobility

**Date:** 8 July 2026

---

Executive summary

Ghana’s ambition to become a 24‑hour economy requires co‑design of transport and energy infrastructure. This paper explains the technical building blocks (ITS, smart grid, and EV charging networks), presents sector-specific strategies for Housing, Logistics Parks, and Commercial Real Estate, and shows concrete, numerical examples (charger counts, storage sizing, expected loads, business models). Key recommendations: pilot integrated hubs combining DC fast chargers (DCFC), PV and battery energy storage systems (BESS); mandate EV‑ready wiring in new developments; adopt open interoperability standards (OCPP, ISO15118); and use tariff design and managed charging to avoid distribution-level overloads.

1. Introduction and scope

- Purpose: provide engineers, investors and policymakers with implementable designs and decisions that enable reliable 24/7 transport services without destabilizing the grid.
- Scope: technical architectures, pilot sizing and examples, safety/standards, business/finance models, regulatory asks and a practical phased roadmap to national deployment.

2. Why transport and energy must be co‑designed

- Core observation: electrification of transport shifts energy demand to new temporal patterns — nightly charging for passenger EVs and continuous or peak episodic charging for freight and buses.
- Opportunity: EVs can be controlled (managed charging/V2G) so they become grid-flexibility assets rather than liabilities.
- Risk if not coordinated: localized transformer overloads, voltage regulation problems, increased losses and higher cost-of-service that lead to negative investor signals.
- Practical example: A neighbourhood transformer rated at 250 kVA serving 200 homes — adding 20 simultaneous 7 kW home chargers (140 kW) can push load beyond the transformer thermal limit during evening peaks without managed charging or storage.

3. Key technical building blocks — expanded with examples

3.1 Intelligent Transport Systems (ITS)

- Role: real-time routing, charger demand forecasting, reservation & queuing at hubs, and integration with charge management systems.
- Components & interactions:
  - Sensors (vehicle counters, loop detectors), telematics (fleet GPS + SOC reporting), and cloud/edge analytics.
  - A Charge Orchestration Module that receives predicted arrival windows from ITS and schedules charging sessions to flatten demand.
- Practical example: Logistics park scheduler
  - Input: vehicle ETA and required SOC.
  - Algorithm: allocate charger start times and power levels to ensure full charge by departure time while capping the park’s peak draw to 800 kW.
  - Outcome: reduce peak draw by 40% vs first-come-first-served charging.
- Data requirement: fleet telematics integration (REST APIs), standardized status messages, and local decision logic for failsafe.

3.2 Smart Grid Integration

- Grid-side actions:
  - Advanced metering infrastructure (AMI) and interval meters at charger sites.
  - Distribution transformer monitoring with retrofits where necessary.
- Flexibility tools:
  - Managed charging: schedule or throttle charge power.
  - Dynamic tariffs: time-of-use (TOU) or real-time pricing to incentivize off-peak charging.
  - Local BESS: shave peaks and provide short duration backup.
- Practical sizing example — BESS for a medium logistics hub:
  - Hub with 4 DCFC bays each 150 kW (max instantaneous draw 600 kW).
  - Required to limit on-grid draw to 350 kW.
  - BESS sizing to support peak shaving for a 1 hour event: (600-350) kW * 1 h = 250 kWh usable plus margin → choose a 350 kWh BESS (round up for depth-of-discharge & inefficiencies). Add inverter capacity at ~400 kW.
- Interconnection guidance: follow IEEE 1547 principles for distributed energy resources; ensure anti-islanding and protection coordination.

3.3 EV charging networks (engineered for 24/7 reliability)

- Charger taxonomy:
  - Residential/AC slow: 3.7–7.4 kW (suitable for overnight).
  - Commercial fast/AC: 11–22 kW.
  - DCFC: 50–350 kW (suitable for logistics & quick top-ups).
- Essential site design:
  - Power provisioning: appropriate conductor sizing, transformer capacity checks, selective fusing.
  - Backup & resilience: onsite BESS sized based on expected outage duration and business continuity objectives (e.g., 2 hours of peak load).
  - Remote monitoring and SLAs: telemetry, remote reset, diagnostics, and an O&M SLA guaranteeing >98% uptime for premium hubs.
- Communications & interoperability:
  - OCPP for charge point management (CPMS).
  - ISO 15118 for secure plug & charge and enabling smart charging/V2G.
  - IEC 61851 and IEC 62196 for connector & conductive charging standards.
- Practical example: Shopping mall deployment
  - Mall expects 600 cars/day. Target supply: 10 AC 22 kW chargers (long‑dwell) + 2 DCFC 60 kW (quick top-ups).
  - Expected daily charging energy: assume 10% of visitors charge, average 12 kWh/session → 720 kWh/day.
  - BESS of 200 kWh to manage peak midday usage and participate in demand charge management.

4. Sector-level deployment strategies with worked examples

4.1 Housing (residential, multi-unit)

- Challenges: constrained parking, shared meters, billing and landlord/tenant arrangements.
- Implementation patterns:
  - New-builds: require raceways and conduit, designate 20% of parking EV‑ready (prewired 32 A circuits). Install tenant-facing smart wallboxes with user auth and remote billing integration.
  - Existing developments: retrofit shared parking with a pooled set of smart chargers and load management to allocate power fairly.
- Worked example: 50‑unit apartment block
  - Approach A (full retrofit): Install 10 dedicated 7 kW chargers with load management (phase one) and provide conduit/raceways for future expansion.
  - Energy impact: if each charging session is 7 kW for 4 hours, 10 simultaneous = 280 kWh/day.
  - Load management: schedule EV charging between 22:00–06:00 and throttle per resident to keep transformer load within limits.
  - Billing: smart wallbox reports session kWh to building energy management system; residents billed via monthly invoice or mobile app.
- Policy ask: building code amendment requiring EV‑ready parking in all new residential developments.

4.2 Logistics Parks

- Distinct requirements: high power, short dwell times for heavy vehicles, strong uptime SLAs, and predictable scheduling.
- Technical design pattern:
  - Cluster DCFC stations sized for fleet peak throughput.
  - Dedicated high-capacity distribution feeder(s), onsite BESS and PV for daytime offset.
  - ITS-driven reservation & charging scheduling.
- Worked example: Medium-sized logistics park (fleet of 30 medium trucks)
  - Typical truck battery: 200 kWh. Typical top-up in shift: 100 kWh.
  - If 6 trucks require recharge simultaneously at 150 kW each = 900 kW peak.
  - Grid contract: 1.2 MW feeder to allow margin. If utility cannot upgrade quickly, option is to install 800 kW BESS discharged during overlapping charging windows to cap on-grid draw to 400 kW.
  - BESS sizing: to supply 500 kW for 2 hours = 1,000 kWh usable; add margins → choose 1.3 MWh nominal system.
  - Economics: cost per kWh for DCFC sessions includes energy + fast-charging premium; consider high-volume discounts for fleet operators under subscription models.
- Operational model: mixed private operator with maintenance contract, reservation app linked to fleet telematics. Uptime SLA 99% with redundancies.

4.3 Commercial Real Estate (shopping centers & office parks)

- Customer behavior: long-dwell charging (shopping, work) works well with AC chargers; DCFC used sparingly for emergency top-ups.
- Integration strategy:
  - Tie charger management into building energy management systems (BEMS) to manage demand charges.
  - Revenue share between landlord and operator, or install-to-own and share charging revenue.
- Example: Regional mall
  - Install 12 x 22 kW chargers across parking decks.
  - Peak mall day extra demand estimated at 264 kW if all chargers used simultaneously; use load management to limit per-tenant allocation.
  - Consider co-locating PV on roof for daytime offset (~200 kW PV) to reduce daytime draw.
  - Business model: charging free for purchases above a threshold; or pay-per-use with free first hour to increase dwell time.

5. Standards, safety and cybersecurity — with examples and checklists

5.1 Technical standards to adopt

- IEC 61851: general requirements for electric vehicle conductive charging systems.
- IEC 62196: plugs, sockets and vehicle couplers (Type 2 preferred in Ghana/EU contexts).
- ISO 15118: secure communication and plug & charge.
- OCPP v1.6+/2.0: for remote CPoMS features.
- IEEE 1547: DER interconnection (BESS/solar).
- Example compliance checklist for a DCFC hub:
  - Conductor sizing certification, transformer protection settings adjusted, surge arrestors installed, earthing and bonding checked, and proper signage and cable management per IEC rules.

5.2 Safety measures

- Fire safety: thermal runaway planning for BESS, fire suppression clearances around DCFC units.
- Earthing: equipotential bonding, lightning protection for outdoor stations.
- Emergency stop and isolation switches accessible at every station.

5.3 Cybersecurity

- Device authentication: TLS mutual authentication for CPMS to charger.
- Firmware handling: secure boot, signed firmware updates.
- Network segmentation: separate operational network for chargers from public Wi‑Fi, restrict remote admin to VPNs or bastion hosts.
- Example incident response: charger compromised — automated isolate-and-quarantine policy triggers, operator alerted within 1 minute, remote session termination.

6. Economic & business models — detailed examples

6.1 Revenue streams: direct energy sales, parking and premium services, value-adds (advertising & retail tie-ins), demand response payments.
6.2 Financing structures:
- Capital purchase & O&M contract: property owner buys hardware, outsources O&M.
- Managed services: operator installs & runs chargers, amortizes hardware cost via revenue share.
- Energy Service Agreement (ESA): third-party finances PV+BESS and sells energy services to host.
- Example financials — mall 12 x 22 kW chargers:
  - CapEx estimate (chargers + installation + civil works): US$120k–$180k.
  - Annual energy sales: 720 kWh/day * 365 = 262,800 kWh/year. At $0.10/kWh revenue = $26k/yr (additional parking fees & advertising increase revenue).
  - Payback depends heavily on tariff & utilization; consider grants/subsidies for early months.

6.3 Risk allocation

- Grid upgrade risk: commonly on utility; consider cost-sharing agreements or developer-paid upgrades with utility rebates.
- Uptime & maintenance: long-term O&M contract with KPIs and penalties for outages to protect service reliability.

7. Deployment roadmap — fleshed out timeline and concrete pilots

Phase 0 — Policy & standards (0–6 months)
- Actions: national EV readiness guideline, building code update, pilot procurement framework, set OCPP/ISO15118 as recommended protocols, create sample procurement & SLA templates.

Phase 1 — Demonstration (6–18 months)
- Pilot 1 (Logistics): 4 x 150 kW DCFC + 350 kWh BESS + 150 kW PV at a priority logistics park on Tema–Accra corridor. Objective: prove scheduling integration with fleet telematics. Metrics: 98% charger uptime, 30% grid peak reduction.
- Pilot 2 (Residential): 50‑unit EV‑ready development in Accra with 10 smart wallboxes and managed charging. Objective: prove multi-tenant billing & fairness algorithms.
- Pilot 3 (Commercial): Mall pilot with 10 AC chargers + 2 DCFC + 200 kWh BESS to demonstrate demand charge mitigation.
- Implementation: procurement using standard RFP templates, 12–18 month operations contract for O&M and data sharing with IET-Gh for monitoring.

Phase 2 — Scale (18–48 months)
- Rollout across priority corridors (Accra–Tema, Accra–Kumasi), major malls, ports and logistics parks.
- Introduce supportive tariffs and concession incentives.

Phase 3 — Market maturity (48+ months)
- Integration of V2G for grid services if vehicles and policy support permits.
- Fleet electrification for buses and heavy vehicles, expanded local manufacturing/assembly for chargers and BESS O&M training.

8. KPIs and monitoring — definitions & targets

- Charger availability: percent uptime measured monthly (target >98% for DCFC hubs).
- Utilization: sessions/day per charger.
- Peak grid draw reduction achieved via BESS/managed charging (%).
- Average waiting time at hubs (minutes).
- Mean time to repair (MTTR) for charger hardware (target <24 hours for urban hubs).
- CO2 equivalent savings per year (tonne CO2e) vs baseline diesel consumption.

9. Risks, sensitivities & mitigations — with examples

- Risk: Low utilization (investor risk).
  - Mitigation: Start with anchor tenants (logistics fleets), implement subscription-based revenue models with guaranteed minimum usage.
- Risk: Grid capacity constraints.
  - Mitigation: BESS and managed charging; stage upgrades with utility cost-sharing.
- Risk: High capex for DCFC + BESS.
  - Mitigation: blended finance: concessional loans, green guarantees, viability gap funding for initial hubs.

10. Concrete recommendations (policy & investor asks)

- Regulatory:
  - Update building code: all new residential and commercial developments to be “EV‑ready” (prewired parking) from 2027.
  - Publish national EV interoperability & safety guidelines referencing OCPP, ISO 15118, IEC standards.
- Financial instruments:
  - Create pilot co-financing window supporting bundled projects that include chargers + PV + BESS.
  - Provide tax incentives or accelerated depreciation for early private investors in public chargers.
- Institutional:
  - Establish an IET-supported technical task group to certify installations and manage pilot monitoring.
- Market:
  - Prioritize logistics parks and high-footfall malls for first-phase investments to secure utilization and visible value.

Appendices

Appendix A — Worked technical sizing examples (quick reference)

Example 1 — Residential: 50-unit building (10 chargers)
- Charger type: 10 x 7 kW smart AC wallboxes.
- Daily energy (if each used once for 4h at 7 kW): 10 * 7 * 4 = 280 kWh.
- Transformer check: existing transformer 250 kVA. Use load management to sequence charging so additional peak < 50 kW during evenings.
- Smart charging rule: allow each resident a 2 kW guaranteed share and additional charge by queue-based allocation if headroom exists.

Example 2 — Logistics hub: 4 x 150 kW DCFC + fleet schedule
- Peak instantaneous power: 600 kW.
- Grid constraint: limit to 350 kW on-grid draw.
- BESS: supply 250 kW for 1 hour → 250 kWh usable; add margin → 350 kWh BESS with 400 kW inverter.

Example 3 — Mall: 12 x 22 kW AC, 2 x 60 kW DCFC
- Max draw if all AC used + DCFCs: (12*22) + (2*60) = 264 + 120 = 384 kW.
- Use BEMS and smart scheduling to avoid simultaneous peak; provision 200 kWh BESS for demand charge mitigation.

Appendix B — Sample procurement / SLA items (high level)
- Availability SLA: 98% uptime for DCFC hubs, 95% for AC chargers.
- MTTR: repair within 24 hours (urban hubs), 72 hours rural.
- Data sharing: CPMS to share anonymized session data with IET‑Gh for monitoring.
- Warranty: 36 months for chargers; BESS performance warranty (80% capacity retention at 10 years or prorated).

Appendix C — FAQ (for Q&A)
Q: Will EV charging cause power outages?
A: Not if charging is managed. Use TOU pricing, managed charging and BESS to smooth peaks. Pilot examples show 30–50% peak shaving achievable with modest BESS.

Q: How expensive is a DCFC hub?
A: DCFC hardware per 150 kW bay (incl. civil works) varies widely; rough installed cost in Ghana context: US$50k–$120k per bay depending on grid upgrade needs and site complexity. Bundling BESS and PV increases CapEx but reduces operating energy cost and demand charge exposure.

Q: Who pays for grid upgrades?
A: Often shared. Early-stage agreements should define cost-share: utility upgrades for distribution backbone; developer pays local reinforcement; government grants or concessional loans can bridge the gap.

Appendix D — Suggested speaking notes (12–15 minutes)
- Opening (30–45 sec): Set the scene with Ghana’s 24‑hour aspiration. State practical focus: how to deliver reliable 24/7 EV charging and integrated mobility hubs.
- Problem (1.5–2 min): Show the grid-plus-transport interaction with a quick transformer example.
- Solution (4 min): Present architecture—smart charging, BESS, PV, ITS scheduling—use the logistics park worked example to show numbers.
- Sector highlights (3 min): One clear action for housing, logistics and commercial real estate (e.g., require EV‑ready wiring; pilot hub on Tema corridor; mall demand-management pilot).
- Policy ask & investment case (2 min): Standards adoption, pilot co-finance, clarify grid-upgrade allocation.
- Close & call to action (30 sec): Establish a technical task group; start 3 pilot projects within 6–12 months.

References & further reading (select)
- IEC standards (61851, 62196), ISO 15118, OCPP specifications.
- IEEE 1547 DER interconnection guidelines.
- IEA Global EV Outlook (for comparative figures on energy use per EV).

---

# Author profile

**Rev. Engr. Dr. Frimpong Kyeremeh**

Rev. Engr. Dr. Frimpong Kyeremeh holds a Doctor of Engineering (D.Eng.) in Power Engineering and Automation from Nanjing University of Technology, China, an MSc in Electrical and Electronics Engineering from the University of Bradford, United Kingdom, and a Bachelor of Technology Education (B.Ed Tech) in Applied Electrical/Electronic from the University of Education, Winneba, Ghana. Dr. Frimpong is a Certified Competency-Based Training (CBT) Curriculum Developer, a certified Building Energy Performance Assessor, and a Platinum AI Trainer and Consultant. He has also received training in Electric Vehicle technologies from Fanshawe College, London Ontario, Canada.

He is the foundation Director of the Centre of Excellence in Electric Vehicles and Green Technologies at Sunyani Technical University. He is also a Senior Lecturer in the Department of Electrical/Electronic Engineering at STU, where he has served for over 20 years.

His research interests include New Energy Vehicles, Renewable Energy Systems, Green Hydrogen, Microgrids, Robotics, Machine Learning, AI in Pedagogy, and TVET Curriculum Development.

Rev. Engr. Dr Kyeremeh is a Fellow of the Institution of Engineering and Technology, Ghana, and is currently the Chairman of the Middle Belt Sector and a council member. Prior to these, Engr. Frimpong served as the Bono Regional Coordinator for the institution from 2021 to 2025.

He has extensive project management experience and has contributed significantly to advancing technical and vocational education in Ghana. With over 20 years of teaching experience in Electrical/Electronic Engineering, Rev. Engr. Dr Kyeremeh is committed to driving innovation in electric mobility and sustainable energy solutions in Ghana and beyond.

Additionally, he is an ordained minister serving as the Minister-in-Charge of the Presbyterian Missionary Worship Centre in Sunyani, Presbyterian Church of Ghana.
