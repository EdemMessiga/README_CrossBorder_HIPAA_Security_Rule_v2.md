# HIPAA Security Rule Gap Assessment CrossBorder Health Analytics Inc.


## Plain-Language Summary

This project simulates a security compliance review for a fictional Toronto-based health data analytics company that had recently begun receiving patient health records from a network of American hospitals. In the United States, any company that receives or processes patient health information on behalf of a hospital must comply with the Health Insurance Portability and Accountability Act, regardless of where that company is located. A formal legal agreement between the two organizations could not be signed until the Canadian company demonstrated it met those requirements.

The review found that the company had been receiving patient data since March 2026 without completing the required security assessment first, meaning legal obligations were already active before any of the necessary controls were in place. The most serious gaps were that no formal analysis of risks to patient data had ever been conducted, that there was no documented procedure for notifying the hospital if a data breach occurred, that three software vendors handling patient data had no legal agreement in place to protect that data, and that servers containing patient information could be accessed using only a password with no second verification step.

This report documents all findings in order of urgency, explains why each gap blocks the legal agreement from being signed, and provides a phased remediation plan to achieve full compliance by the target contract execution date of July 31, 2026.

**Framework:** HIPAA Security Rule (45 CFR Part 164, Subpart C) + HITECH Act (2009)
**Industry:** Health Technology / Analytics Canadian SaaS with US Healthcare Clients
**Entity (Fictional):** CrossBorder Health Analytics Inc. Toronto-based health data analytics SaaS
**HIPAA Role:** Business Associate creates, receives, maintains, and transmits ePHI on behalf of covered entity clients
**Assessment Type:** Internal HIPAA Security Rule Gap Assessment (pre-BAA execution)
**Assessor:** Edem Messiga, ISO 27001 Certified Lead Auditor Privacy and Security Office
**Assessment Period:** May 1 to 23, 2026 (15 business days)
**BAA Execution Target:** July 31, 2026 (MidWest Health System 14 hospitals, Illinois)

---

## Why HIPAA for a Canadian GRC Portfolio?

Canadian health technology companies are increasingly entering the US market and every Canadian company that receives US patient health data on behalf of a US hospital, health plan, or healthcare provider becomes a HIPAA Business Associate. This is one of the most common GRC scenarios for Canadian health IT practitioners: a company that grew serving Canadian clients now has its first US healthcare customer, and suddenly the HIPAA Security Rule applies.

This project simulates a real-world scenario: a Toronto-based health analytics company has been receiving US ePHI since March 2026 under a pilot agreement, without first completing a HIPAA Security Rule compliance assessment. Now, the formal contract requires a BAA and the gap assessment reveals the company is not ready. This is the situation many Canadian health tech companies actually face.

---

## Engagement Context

CrossBorder Health Analytics processes population health analytics for US hospital networks and health plans. Its first major US client MidWest Health System (14 hospitals, Illinois) has a contract contingent on executed BAA and demonstrated HIPAA Security Rule compliance by July 31, 2026.

CrossBorder began receiving ePHI (2.4M patient records claims, labs, diagnoses, medications) under a pilot agreement in March 2026. This means HIPAA obligations are already in effect any breach from that date onward triggers HITECH mandatory notification obligations.

**The conclusion: BAA execution is currently blocked by 14 of 17 remediation actions.**

---

## Key Findings

| Ref | Domain | Finding | Spec Type | Rating |
|---|---|---|---|---|
| HA-ADM-02 | Administrative | No ePHI-scoped risk analysis 2025 analysis predates ePHI receipt | Required | **Critical** |
| HA-ADM-07 | Administrative | No HIPAA breach notification procedure HITECH §13402 obligations unmet | Required | **Critical** |
| HA-ADM-10 | Administrative | 3 subcontractor BAs (Snowflake, Databricks, CloudLink) without BAAs | Required | **Critical** |
| HA-TEC-07 | Technical | SSH MFA not enforced production servers have ePHI-permissioned IAM roles | Addressable | **Critical** |
| HA-PHY-03 | Physical | 9 ePHI-access developer laptops without MDM encryption unconfirmed, no EDR | Required | **Critical** |
| HA-ADM-04 | Administrative | No HIPAA-specific workforce training for 9 ePHI-handling staff | Addressable | High |
| HA-ADM-05 | Administrative | 4 staff with ePHI access exceeding minimum necessary standard | Addressable | High |
| HA-TEC-04 | Technical | Shared Snowflake emergency credential in LastPass no audit trail | Required | High |
| HA-PHY-05 | Physical | No ePHI return or destruction procedure for BAA termination | Required | High |
| HA-TEC-05 | Technical | Databricks audit log retention only 90 days should be minimum 1 year | Required | High |

**Overall:** 10 of 32 controls Compliant | 22 Gap or Partial | 8 Critical findings
**BAA Blockers:** 14 of 17 remediation actions

---

## Deliverables

| File | Description |
|---|---|
| `CrossBorder_HIPAA_Security_Rule_Workbook.xlsx` | 4-tab workbook: Engagement Overview (safeguard domains, specification type reference, findings summary with compliance rate formula), Security Rule Assessment (28 controls with CFR section, Required vs Addressable designation, audit procedure, evidence, finding, risk rating, root cause, BA implication, recommended action, BAA blocker column), Risk Register (12 risks with NIST SP 800-30 likelihood-impact scoring), Remediation Plan (17 actions with BAA blocker designation and target dates) |
| `CrossBorder_HIPAA_Security_Rule_Report.docx` | Formal gap assessment report: BAA execution at-risk escalation notice, HIPAA BA obligations for Canadian entities, 4 detailed Critical findings with OCR enforcement context, domain-by-domain findings summary, HIPAA-PHIPA-PIPEDA alignment table (3-framework crosswalk), BAA execution timeline, HHS OCR enforcement context with CMP tier table, report approval page |

---

## How HIPAA Applies to a Canadian Company

This is the most common misconception corrected in this project: Canadian companies are not exempt from HIPAA. HIPAA obligations flow from the covered entity (the US hospital) to any entity handling ePHI on the covered entity's behalf regardless of where that entity is incorporated.

**The key legal chain:**
1. MidWest Health System (covered entity) is subject to HIPAA
2. CrossBorder receives ePHI from MidWest Health System to perform analytics services
3. CrossBorder is therefore a Business Associate under 45 CFR §164.103
4. Canadian incorporation does not affect this status (confirmed by external HIPAA counsel)
5. CrossBorder must comply with the full HIPAA Security Rule as a Required BA safeguard

This chain applies to any Canadian company that: processes US patient records, provides analytics to US hospitals/health plans, operates as a cloud service provider for US healthcare clients, or handles US health data in any electronic form.

---

## HIPAA Security Rule Structure

The HIPAA Security Rule has three safeguard categories containing both **Required** and **Addressable** specifications:

| Specification Type | What It Means | CrossBorder Implication |
|---|---|---|
| Required | Must be implemented no flexibility | All Required specs must be in place before BAA execution |
| Addressable | Must implement OR document why an equivalent alternative is used | If not implementing, must document justification and describe equivalent |

**Important:** "Addressable" does NOT mean optional. An organization that decides not to implement an addressable specification must document the reason and describe the equivalent alternative measure implemented instead. This documentation itself is a Required obligation.

---

## HIPAA-PHIPA-PIPEDA Three-Framework Alignment

| Control Area | HIPAA Security Rule | PHIPA (Ontario) | PIPEDA |
|---|---|---|---|
| Risk Analysis | Required annually (§164.308(a)(1)) | Expected under s.12 safeguards | Implied under Principle 7 |
| Breach Notification | CE notification ≤60 days; HHS OCR reporting | IPC + individuals (s.12(2)) | OPC + individuals for RROSH |
| Encryption at Rest | Addressable implemented as best practice | s.12 proportionate safeguards | Principle 7 (sensitive health data) |
| Access Controls | Required unique IDs, minimum necessary | s.29 minimum necessary | Principles 4 and 7 |
| Audit Logging | Required §164.312(b) | s.10 audit trail for PI access | Principle 7 (safeguards) |
| Workforce Training | Addressable HIPAA-specific awareness | s.12 agents informed of obligations | Principle 1 (accountability) |
| Business Associate / Agent | BAA required (§164.308(b)) | DPA with agents (by analogy) | Principle 1 third-party accountability |
| Documentation Retention | 6 years from creation/last effective date | Regulation 114/94 (healthcare records) | Principle 5 as long as necessary |

The alignment means that CrossBorder's HIPAA remediation simultaneously advances PHIPA and PIPEDA compliance all three frameworks can be addressed in a unified security investment program.

---

## HHS OCR Enforcement Patterns

The following findings in this project are the most frequently cited in HHS OCR HIPAA enforcement actions:

| Finding | OCR Enforcement History |
|---|---|
| No risk analysis | Single most common OCR finding; cited in virtually every Resolution Agreement since 2012 |
| Subcontractor BAAs missing | Multiple enforcement actions involving cloud-based BAs and their subcontractors |
| Inadequate access controls | Authentication gaps and minimum necessary violations cited in multiple settlements |
| No breach notification procedure | Failure to notify CE within 60 days has resulted in significant penalties |
| No workforce training | Cited as independent violation in multiple OCR audit findings |

**Civil Monetary Penalties (2023 adjusted amounts):**
- Tier 1 (Did Not Know): $137 to $68,928 per violation; $2.07M annual cap
- Tier 2 (Reasonable Cause): $1,379 to $68,928 per violation; $2.07M annual cap
- Tier 3 (Willful Neglect, Corrected): $13,785 to $68,928 per violation; $2.07M annual cap
- Tier 4 (Willful Neglect, Not Corrected): $68,928 to $2.07M per violation; $2.07M annual cap

CrossBorder's current state (receiving ePHI since March 2026 without completed risk analysis, breach notification procedure, or subcontractor BAAs) could be characterized as Tier 3 or 4 willful neglect if a breach occurs. Executing the remediation plan promptly demonstrates reasonable diligence positioning CrossBorder in Tier 1 or 2.

---

## BAA Execution Timeline

| Phase | By | Key Actions |
|---|---|---|
| Phase 1: Immediate | June 15, 2026 | Revoke excess ePHI access; begin risk analysis; risk treatment plans |
| Phase 2: Technical | June 30, 2026 | SSH MFA; MDM for 9 laptops; 3 subcontractor BAAs; emergency access; log retention; AUP update |
| Phase 3: Documentation | July 15, 2026 | ePHI risk analysis; IRP update; HIPAA Security Policy; documentation package |
| Phase 4: Training | July 15, 2026 | HIPAA training 100% completion for ePHI-access staff |
| BAA Execution | July 31, 2026 | Execute BAA with MidWest Health System; provide documentation package |

---

## What Makes This Project Realistic

**The "already receiving ePHI without HIPAA compliance" scenario is real.** Many Canadian companies enter the US healthcare market via a pilot agreement before their legal team finishes the compliance assessment. This project reflects that reality CrossBorder has HIPAA obligations already in effect, not "pre-contract." This changes the urgency framing: the assessment is not preparation, it is remediation.

**Required vs Addressable is applied correctly throughout.** Every finding specifies whether the CFR section is Required or Addressable a distinction that matters significantly for enforcement. The risk analysis gap (Required) and the breach notification gap (Required) cannot be addressed with equivalent alternatives. The SSH MFA gap (Addressable) technically could be but in practice, OCR has consistently expected MFA as the standard implementation of §164.312(d).

**The HHS OCR enforcement context section is practical, not theoretical.** Including actual CMP tier ranges with 2023 adjusted figures, and connecting them to CrossBorder's specific current state, shows the business consequence of inaction. This is how a GRC practitioner makes a risk-based case to a CEO not as abstract compliance language, but as a quantifiable financial exposure.

**The HIPAA-PHIPA-PIPEDA crosswalk demonstrates multi-framework fluency.** A Canadian health tech practitioner who can show a hiring manager that HIPAA remediation simultaneously advances PHIPA and PIPEDA compliance and can explain why is more valuable than one who treats each framework as a separate silo.

---

## Lessons Learned

**HIPAA obligations attach to the ePHI, not the contract.** CrossBorder began receiving ePHI in March 2026 under a pilot agreement. Many practitioners assume HIPAA obligations start when the formal BAA is signed. This is wrong HIPAA obligations attach when ePHI is first received, regardless of contract status. The BAA is the documentation of an obligation that already exists.

**The risk analysis is the foundation of everything.** HHS OCR's enforcement statistics consistently show that risk analysis is the single most common HIPAA deficiency. This is not a coincidence a proper ePHI-scoped risk analysis drives the entire Security Rule implementation: it identifies what threats exist, what controls are needed, what is reasonable and appropriate, and what residual risk is accepted. Without it, every other control decision is arbitrary.

**Subcontractor BAA chains are often the last thing companies think about and the first thing OCR checks.** CrossBorder's use of Snowflake, Databricks, and an informal integration vendor without BAAs is a common pattern in cloud-native health tech companies. The remediation for Snowflake and Databricks is simple both vendors have standard HIPAA BAAs available in their customer portals and executable within 24 hours. The CloudLink situation (no contract at all) is more serious and requires immediate legal engagement.

**For Canadian companies: HIPAA and Canadian health privacy are more aligned than practitioners expect.** Every hour invested in HIPAA Security Rule compliance simultaneously advances PHIPA and PIPEDA compliance. Framing security investment as a unified program rather than separate HIPAA, PHIPA, and PIPEDA workstreams saves resources and produces stronger results.

---

## Related Projects

| Repository | Framework |
|---|---|
| [GRC-PCI-DSS-v4-MapleFinancial](../GRC-PCI-DSS-v4-MapleFinancial) | PCI-DSS v4.0 Canadian Regional Bank |
| [GRC-SOC2-TypeI-CareSync](../GRC-SOC2-TypeI-CareSync) | SOC 2 Type I Healthcare SaaS (EHR platform, PHIPA) |
| [GRC-ISO27001-GovTech-Ontario](../GRC-ISO27001-GovTech-Ontario) | ISO 27001 Provincial Government Digital Services |
| [GRC-NIST-CSF-NovaSaaS](../GRC-NIST-CSF-NovaSaaS) | NIST CSF 2.0 Canadian B2B SaaS company |
| [GRC-PIA-PIPEDA-CanRetail](../GRC-PIA-PIPEDA-CanRetail) | PIA Canadian Retail Loyalty Program (PIPEDA + Quebec Law 25) |

---

## About the Author

**Edem Messiga**
ISO 27001 Certified Lead Auditor | Cybersecurity GRC | Bilingual EN/FR
[linkedin.com/in/edem-messiga](https://linkedin.com/in/edem-messiga)

> All entities, patient data references, client names, financial figures, and individuals in this project are fictional and created for professional portfolio and development purposes only. No real patient data, organizations, or HIPAA enforcement actions are represented.
