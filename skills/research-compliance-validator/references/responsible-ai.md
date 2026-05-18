# Responsible AI & Research Ethics Checklist

References: UNESCO AI Ethics Recommendation (2021), NIST AI RMF (2023), IEEE Ethically Aligned Design, Belmont Report principles, EU HLEG Trustworthy AI Guidelines

## Fairness & Non-Discrimination
- [ ] **Demographic representation assessed**: The dataset or study sample is examined for over/under-representation of demographic groups (age, gender, race, disability, socioeconomic status)
- [ ] **Fairness metrics defined**: Relevant fairness metrics (e.g., equal opportunity, demographic parity) are chosen and measured for any model or analysis
- [ ] **Bias mitigation applied**: Steps are taken to mitigate identified biases in data collection, model training, or analysis
- [ ] **Impact on vulnerable groups considered**: Potential harms to vulnerable or marginalised groups are explicitly considered and documented

## Accountability & Governance
- [ ] **Roles and responsibilities defined**: Clear ownership of the research project's ethical compliance is assigned (PI, ethics officer, DPO, etc.)
- [ ] **Ethics review conducted**: The project has undergone institutional ethics review (IRB, ethics committee) where required
- [ ] **Decision audit trail maintained**: Key decisions (data choices, model choices, exclusion criteria) are logged with rationale
- [ ] **Incident response plan exists**: A process exists to handle ethical incidents, complaints, or unexpected harms

## Transparency & Openness
- [ ] **Methodology documented**: Research methods are documented in enough detail to be reproducible
- [ ] **Limitations disclosed**: Limitations of the data, methods, and findings are clearly communicated
- [ ] **Conflicts of interest disclosed**: Funding sources and potential conflicts of interest are declared
- [ ] **Model cards / data sheets produced**: For AI systems or datasets, a model card or datasheet describing purpose, limitations, and intended use is created

## Explainability & Interpretability
- [ ] **Model choices justified**: The choice of algorithm/model is justified in terms of interpretability vs. performance trade-offs
- [ ] **Predictions explainable to stakeholders**: For consequential decisions, explanations can be provided to affected individuals
- [ ] **Black-box risks acknowledged**: If using black-box models, the risks and mitigations of opaque decision-making are acknowledged

## Privacy & Data Dignity
- [ ] **Participant dignity respected**: Data collection and use respects participants' dignity and does not demean or exploit
- [ ] **Re-identification risk assessed**: The risk of re-identifying anonymised individuals from the dataset has been assessed
- [ ] **Data sharing agreements in place**: If data is shared with third parties, agreements are in place governing use, access, and security
- [ ] **Secondary use disclosed**: If data collected for one purpose may be reused, participants are informed

## Safety & Do No Harm
- [ ] **Harm assessment conducted**: Potential harms to participants, third parties, and society from the research outputs are identified
- [ ] **Risk-benefit analysis documented**: Benefits of the research are weighed against potential harms
- [ ] **Dual-use risks considered**: The research outputs cannot easily be misused for harmful purposes, or mitigations are in place
- [ ] **Participant safety protocols**: Protocols exist for handling participant distress, adverse events, or data breaches

## Inclusivity & Participation
- [ ] **Affected communities consulted**: Where feasible, communities affected by the research have been involved in its design
- [ ] **Accessible outputs**: Research findings are communicated in forms accessible to non-specialist audiences where relevant
- [ ] **Diverse research team**: The research team's composition is considered with respect to diversity of perspective

## Environmental Sustainability
- [ ] **Compute footprint considered**: Energy consumption of model training and data processing is acknowledged and minimised where possible
- [ ] **Sustainability reported**: If significant compute was used, the carbon footprint is estimated and reported

## Scoring guidance
- Pass: Clear evidence in project files or process documentation
- Partial: Mentioned or partially implemented
- Fail: Not addressed or clear gap
- N/A: Not applicable to this research type
