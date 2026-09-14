# SecAI+ (CY0-001) Curriculum & Exam Cram Mapping

Source of truth: [CompTIA SecAI+ (V1) exam objectives](https://www.comptia.org/en-em/certifications/secai/#overview)

## Exam Details

| Item | Detail |
|------|--------|
| Exam version | V1 |
| Series code | CY0-001 |
| Launch date | February 17, 2026 |
| Questions | Maximum of 60, multiple-choice and performance-based |
| Duration | 60 minutes |
| Passing score | 600 (on a scale of 100–900) |
| Languages | English and Japanese |
| Recommended experience | 3–4 years in IT, 2+ years hands-on cybersecurity; Security+, CySA+, PenTest+, or equivalent |
| Retirement | Estimated 3 years after launch |

---

## Domain 1.0 — Basic AI Concepts Related to Cybersecurity (17%)

- **1.1 Explain core AI principles and terminology**: Machine learning, deep learning, natural language processing, and automation.
- **1.2 Identify AI applications in security**: Use cases for AI in threat detection, defense, and security operations.
- **1.3 Recognize AI-driven threats**: Automated phishing, polymorphic malware, adversarial machine learning, and malicious use of generative AI.

### Cram Mapping

| Objective | Topics | Cram Coverage |
|-----------|--------|---------------|
| 1.1 Core AI principles & terminology | ML, deep learning, NLP, transformers, GANs, LLMs/SLMs; supervised/unsupervised/RL/federated learning; fine-tuning, pre-training, pruning, quantization; model validation, k-fold cross-validation, overfitting, concept drift, data poisoning | `chapter-1-exam-cram-v1.2.md` § 1.1 (AI Types & Techniques) |
| 1.2 AI applications in security | Threat detection, intrusion detection, UEBA, phishing classification, log analysis, Isolation Forest, autoencoders, RL response agents, prompt engineering for security workflows | `chapter-1-exam-cram-v1.2.md` § 1.1 (Anomaly Detection Models, RL Deep Dive), § 1.2 (Prompt Engineering), § 1.4 (AI Offensive & Defensive Use) |
| 1.3 AI-driven threats | Automated phishing, polymorphic malware, adversarial ML, malicious generative AI | `chapter-1-exam-cram-v1.2.md` § 1.4; cross-referenced with `chapter-5-exam-cram-v1.2.md` § 5.3 |

---

## Domain 2.0 — Securing AI Systems (40%)

- **2.1 Implement security controls**: Protect AI systems, data, and models using robust technical safeguards.
- **2.2 Secure AI deployment environments**: Apply best practices across on-premises, cloud, and hybrid infrastructures.
- **2.3 Mitigate adversarial risks**: Defend against attacks targeting AI models, data pipelines, and inference layers.

### Cram Mapping

| Objective | Topics | Cram Coverage |
|-----------|--------|---------------|
| 2.1 Implement security controls | Threat modeling frameworks (OWASP LLM/ML Top 10, MITRE ATLAS, NIST AI RMF, STRIDE, DREAD, MAESTRO); model/gateway controls; guardrails (PII redaction, prompt injection, jailbreak, secrets detection); rate limits, token limits, input/quantity quotas, modality limits; access control mechanisms (RBAC, throttling, content filtering); endpoint security; agent/tool security; cryptography (KMS, TPM, HSM, TEE, homomorphic encryption, DP-SGD); data protection/masking/DLP; logging & audit telemetry | `chapter-2-exam-cram-v1.2.md` (Threat Modeling, Security Controls, Gateway Controls); `chapter-3-exam-cram-v1.2.md` § 3.1–3.7 (Access Controls, Cryptographic & Privacy Techniques, Data Protection, Logging) |
| 2.2 Secure AI deployment environments | On-prem vs pre-trained vs vendor models evaluation; AI gateway architecture; deployment isolation; sanctioned vs unsanctioned (Shadow AI); public vs private model deployments (multi-tenant SaaS vs isolated VPC/on-prem) | `chapter-2-exam-cram-v1.2.md` (Model Evaluation, AI Gateway Controls); `chapter-6-exam-cram-v1.2.md` § 6.6 (Model Sourcing, Shadow AI & Deployment Architectures) |
| 2.3 Mitigate adversarial risks | AI lifecycle attacks; poisoning, backdoor, trojan attacks; model inversion, membership inference, model theft; evasion, output handling, excessive agency; CoT manipulation, model skewing, model DoS; compensating controls matrix; RAG/vector store protections; data handling techniques (cleansing, verification, lineage, provenance, integrity, augmentation, balancing) | `chapter-4-exam-cram-v1.2.md` § 4.1–4.5 (AI Lifecycle, Attack Vectors, Compensating Controls); `chapter-1-exam-cram-v1.2.md` § 1.3 (Data Security for AI, RAG, Data Processing Techniques); `chapter-2-exam-cram-v1.2.md` (OWASP ML Top 10 attack types) |

---

## Domain 3.0 — AI-Assisted Security (24%)

- **3.1 Enhance detection and response**: Use AI-driven tools to identify anomalies, detect threats, and accelerate incident remediation.
- **3.2 Automate security workflows**: Integrate AI for event triage, alert correlation, and response orchestration.
- **3.3 Apply AI techniques in operations**: Incorporate AI into threat modeling, behavior analysis, and continuous monitoring.

### Cram Mapping

| Objective | Topics | Cram Coverage |
|-----------|--------|---------------|
| 3.1 Enhance detection and response | AI-driven threat detection, pattern analysis for fraud, adaptive honeypots/deception technology, anomaly detection, SOAR-automated playbooks | `chapter-5-exam-cram-v1.2.md` § 5.1 (Defensive Applications); `chapter-1-exam-cram-v1.2.md` § 1.1 (Anomaly Detection Models, RL Deep Dive) |
| 3.2 Automate security workflows | SOAR platforms, event triage, alert correlation, response orchestration, no-code vs low-code environments | `chapter-5-exam-cram-v1.2.md` § 5.1 (SOAR, No-Code vs Low-Code) |
| 3.3 Apply AI techniques in operations | AI threat modeling (STRIDE, MITRE ATLAS), behavioral analysis, continuous monitoring, secure code development/review (linting, SAST, SCA, SBOM, unit/model/regression testing, fuzzing), AI in IDEs, MCP | `chapter-5-exam-cram-v1.2.md` § 5.2 (Secure Code Development, Review & Testing); `chapter-2-exam-cram-v1.2.md` (AI Threat Modeling Overview, Threat Modeling Frameworks) |

---

## Domain 4.0 — AI Governance, Risk, and Compliance (19%)

- **4.1 Understand regulatory frameworks**: Identify global governance requirements and their implications for AI adoption.
- **4.2 Integrate GRC into AI projects**: Incorporate governance, risk management, and compliance practices throughout the AI lifecycle.
- **4.3 Ensure responsible AI use**: Apply ethical guidelines, legal standards, and industry frameworks such as GDPR and NIST AI RMF.

### Cram Mapping

| Objective | Topics | Cram Coverage |
|-----------|--------|---------------|
| 4.1 Understand regulatory frameworks | EU AI Act risk tiers, OECD AI principles, ISO/IEC 42001/23894/22989/5338, NIST AI RMF (Govern/Map/Measure/Manage), GDPR, HIPAA, PCI-DSS | `chapter-6-exam-cram-v1.2.md` § 6.5 (Regulatory Frameworks, Standards & Compliance); `chapter-3-exam-cram-v1.2.md` § 3.2 (Standards, Frameworks & Regulatory Compliance) |
| 4.2 Integrate GRC into AI projects | AI CoE positioning models, roles & responsibilities matrix, policies/procedures/technical guardrails, GRC maturity roadmap, human oversight (HITL/HOTL), M-of-N consensus, AI-assisted approvals, gated automated controls, third-party compliance evaluations & audits | `chapter-6-exam-cram-v1.2.md` § 6.1–6.3, § 6.7 (AI CoE, Roles, Policies, Third-Party Evaluations); `chapter-5-exam-cram-v1.2.md` § 5.4 (AI Governance & Human Oversight Patterns) |
| 4.3 Ensure responsible AI use | Responsible AI principles (fairness, accountability, transparency & explainability, privacy & data governance, sustainability, consistency & reliability), model cards, watermarking/content provenance, incident playbooks & reputational risk | `chapter-6-exam-cram-v1.2.md` § 6.4, § 6.7 (Responsible AI Principles, Reputational Risk Governance); `chapter-1-exam-cram-v1.2.md` § 1.3 (Watermarking) |

---

## Cram File Index

| File | Chapter | Primary Domain(s) |
|------|---------|-------------------|
| `chapter-1-exam-cram-v1.2.md` | Ch 1 — AI & Data Concepts for Cybersecurity | Domain 1.0 (17%) |
| `chapter-2-exam-cram-v1.2.md` | Ch 2 — Implementing Threat Modeling and Securing AI Systems | Domain 2.0 (40%) |
| `chapter-3-exam-cram-v1.2.md` | Ch 3 — Installing Access Controls for AI | Domain 2.0 (40%) |
| `chapter-4-exam-cram-v1.2.md` | Ch 4 — Distinguishing AI-Related Threats and Compensating Controls | Domain 2.0 (40%) |
| `chapter-5-exam-cram-v1.2.md` | Ch 5 — Leveraging AI in Security and Understanding Its Misuse | Domain 3.0 (24%) |
| `chapter-6-exam-cram-v1.2.md` | Ch 6 — Understanding AI Governance, Risk, and Compliance | Domain 4.0 (19%) |

**Study weighting guide:** Prioritize Domain 2.0 (40%) — chapters 2–4 combined. Then Domain 3.0 (24%, chapter 5), Domain 4.0 (19%, chapter 6), and Domain 1.0 (17%, chapter 1).

---

## Video Course Mapping — Packt "CompTIA SecAI+ AI Security Certification – Complete Exam Preparation Guide"

Source: [Packt video course (9781808651458)](https://subscription.packtpub.com/video/security/9781808651458/p1). The course's 8 sections are a superset reorganization of the same 4 exam domains; its section 6 title ("Securing AI Systems") actually covers AI-assisted security operations (Domain 3.0 content).

| Course Section | Course Topics | Exam Domain (Weight) | Cram Coverage |
|----------------|---------------|----------------------|---------------|
| **1. Introduction & Exam Overview** | Welcome & course roadmap; what is SecAI+; exam domains, format & scoring strategy | All domains (exam-level context) | `curriculum.md` Exam Details table; `chapter-1-exam-cram-v1.2.md` (domain weight in title) |
| **2. AI Fundamentals for Security** | AI/ML/DL/NLP & generative AI; model types, training vs inference; prompt engineering & AI inputs; AI architecture components | Domain 1.0 (17%) | `chapter-1-exam-cram-v1.2.md` § 1.1 (AI Types & Techniques, Specialized Models, Training Techniques, RL Deep Dive), § 1.2 (Prompt Engineering) |
| **3. AI Lifecycle & Data Security** | AI lifecycle overview; data quality, integrity & lineage; secure training & validation; deployment, monitoring & retirement | Domain 2.0 (40%) + Domain 1.0 support | `chapter-1-exam-cram-v1.2.md` § 1.1 (Model Validation & Risks), § 1.3 (Data Security for AI, Data Processing Techniques); `chapter-3-exam-cram-v1.2.md` § 3.6–3.7 (Data Protection, Logging); `chapter-4-exam-cram-v1.2.md` § 4.1–4.2 (AI Lifecycle Security & Attack Phases) |
| **4. Securing AI Systems** | AI threat landscape; OWASP top risks for AI; MITRE ATLAS & adversarial attacks; threat modeling scenarios | Domain 2.0 (40%) | `chapter-2-exam-cram-v1.2.md` (Threat Intelligence Resources, OWASP LLM/ML Top 10, MITRE ATLAS, Threat Modeling Methods); `chapter-4-exam-cram-v1.2.md` § 4.4–4.5 (Attack Vectors, Compensating Controls) |
| **5. AI-Assisted Security Operations** | Identity, authentication & authorization; encryption, secrets & key management; secure APIs & access controls; model guardrails & prompt security; logging, monitoring & incident response | Domain 2.0 (40%) | `chapter-3-exam-cram-v1.2.md` § 3.1–3.5, § 3.7 (Access Controls, Model Access & Endpoint Security, Agent/Tool Security, Cryptographic Techniques, Logging & Telemetry); `chapter-2-exam-cram-v1.2.md` (Guardrail Types, AI Gateway Controls); `chapter-1-exam-cram-v1.2.md` § 1.2 (Prompt Safety & Guardrails) |
| **6. Securing AI Systems** *(course mislabels this; content = AI-assisted ops)* | AI for threat detection & analytics; automated alerting & response; SOC use cases with AI | Domain 3.0 (24%) | `chapter-5-exam-cram-v1.2.md` § 5.1 (Defensive Applications, Deception Technology, SOAR); `chapter-1-exam-cram-v1.2.md` § 1.1 (Anomaly Detection Models) |
| **7. Governance, Risk & Compliance** | AI governance fundamentals; risk management & controls; ethics, compliance & responsible AI | Domain 4.0 (19%) | `chapter-6-exam-cram-v1.2.md` § 6.1–6.7 (AI CoE, Roles, Policies, Responsible AI, Regulatory Frameworks, Third-Party Evaluations); `chapter-3-exam-cram-v1.2.md` § 3.2 (Standards & Regulatory Compliance) |
| **8. Exam Preparation & Final Review** | Domain-wise revision summary; sample exam questions walkthrough; exam strategy & final tips | All domains | Each cram's **Quick Check** section; `chapter-1-exam-cram-v1.2.md` **Practice Test Failures** (exam-ready takeaways from missed questions); Study Weighting Guide below |

**Course vs. exam coverage note:** The video course maps cleanly onto the official domains except its section 6, whose title duplicates section 4 but whose topics (threat detection, alerting, SOC use cases) belong to Domain 3.0. No course section covers material outside the official objectives — use both as complementary views of the same blueprint: official objectives define *what is tested*; the course sections define *a study sequence*.
