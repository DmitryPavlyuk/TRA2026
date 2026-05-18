# TRA 2026: Responsible AI Agents in Transportation Research

Supporting repository for the presentation:

> **"Responsible AI Agents in Transportation Research: Opportunities and Risks for Ethical and Impactful Innovation"**
> D. Pavlyuk, 20 May 2026, Transport Research Arena 2026

---

## Repository Contents

```
skills/
  research-compliance-validator/   # Example Claude Code skill (see below)
    SKILL.md
    references/
      gdpr.md
      ai-act.md
      responsible-ai.md
TRA_2026_pavlyuk.pdf               # Presentation slides (PDF)
TRA_2026_pavlyuk.pptx              # Presentation slides (PowerPoint)
```

---

## Example Skill: Research Compliance Validator

The [`skills/research-compliance-validator/`](skills/research-compliance-validator/) directory contains a working [Claude Code](https://claude.ai/code) skill that demonstrates agentic AI assistance for research governance.

**What it does:** audits research project files against GDPR, EU AI Act, and Responsible AI / Ethics requirements, then renders an interactive compliance checklist widget in the chat interface.

**Frameworks covered:**
- GDPR (Regulation (EU) 2016/679) — Articles 5, 6, 7, 9, 13, 17, 25, 30, 35
- EU AI Act (Regulation (EU) 2024/1689) — risk tiers, transparency, human oversight, data governance
- Responsible AI / Ethics — fairness, accountability, transparency, explainability, privacy, safety, inclusivity

**To use the skill**, copy the `skills/` directory into a project, then invoke it with a prompt such as:
> *"Validate my research project for GDPR and AI Act compliance"*

---

## Referred TSI Publications

- **InclusiveNet** Framework to Personalise Mobility Solutions for Vulnerable Road Users
  [tsi.lv/projects/inclusivenet-framework-to-personalize-mobility-solutions-for-vulnerable-road-users/](https://tsi.lv/projects/inclusivenet-framework-to-personalize-mobility-solutions-for-vulnerable-road-users/)

- **Extraction of Empty Container Repositioning Rules from a Reinforcement Learning Policy**
  K. Lohina, D. Pavlyuk - presented at TRA-2026

- **LLM-Driven Agentic System for Enhanced Decision Support in Multi-Modal Logistics**
  M. Ilin, D. Pavlyuk - presented at TRA-2026

---

## References

| # | Reference |
|---|-----------|
| 1 | Regulation (EU) 2016/679 - General Data Protection Regulation (GDPR) |
| 2 | Regulation (EU) 2024/1689 - EU Artificial Intelligence Act |
| 3 | UNESCO Recommendation on the Ethics of Artificial Intelligence (2021) |
| 4 | NIST AI Risk Management Framework (AI RMF 1.0, 2023) |
| 5 | IEEE Ethically Aligned Design (EAD1e, 2019) |
| 6 | EU High-Level Expert Group on AI - Ethics Guidelines for Trustworthy AI (2019) |

---

## Contact

Dmitry Pavlyuk - [LinkedIn](http://www.linkedin.com/in/dmitry-pavlyuk)
