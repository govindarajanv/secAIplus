# Chapter 4 - Exam Cram Notes

## Distinguishing AI-Related Threats and Compensating Controls

**Domain Weight:** CompTIA SecAI+ (CY0-001)

---

## 4.1 Security Across the AI Lifecycle

| Phase | Core Security Activities | Key Compensating Controls |
|-------|--------------------------|---------------------------|
| **Design** | Threat modeling, compliance obligation analysis, architecture risk assessment, outage impact on regulated services | Data provenance validation, hash-based immutability checks on raw logs, PII tokenization, outlier detection with tools like IBM Adversarial Robustness Toolbox (ART) |
| **Model Development & Training** | Code hygiene, framework dependency scanning, environment isolation, architecture selection (speed vs. explainability) | Reproducible training pipelines, isolated training networks, adversarial training, strong identity verification and continuous quality scoring for data labelers |
| **Pre-Deployment & Validation** | Reference environment benchmarking, blue-green rollouts, canary releases, SIEM integration | Model registry (versioned records of models, datasets, evaluations), formal change control with documented approvals (SOC manager, model owner, risk owner), rollback plans |
| **Runtime & Deployment** | Live feature monitoring, latency spike tracking, anomaly detection on unusual calls | Automated response playbooks, input isolation for human review, API rate limits, prompt firewalls |
| **Monitoring & Maintenance** | Continuous model drift detection, library patching, periodic red-teaming, threat model re-evaluation | Closed-loop feedback channels channeling false positives and incident reports back to data preparation; scheduled retraining |

**Exam Tip:** The **Model Registry** is the central auditable system of record for tracking model, dataset, and evaluation versions. All high-impact model promotions require documented approvals, designated change windows, active monitoring, and tested rollback plans.

---

## 4.2 Lifecycle Attack Phases & Threat Mapping

| Lifecycle Phase | Primary Threats | Description |
|-----------------|-----------------|-------------|
| **Training Phase** | Data Poisoning, Model Poisoning, Backdoor Injection, Bias Injection | Adversaries manipulate training sets, gradients, or supply chains to distort learning or embed hidden behavior |
| **Inference Phase** | Evasion Attacks, Input Manipulation, Prompt Injection, Jailbreaks, Indirect Prompt Injection | Adversaries craft adversarial inputs to bypass controls, force misclassification, or override model constraints |
| **Deployment Phase** | Model Theft, Model Inversion, Membership Inference, AI Abuse, Model DoS | Adversaries reverse-engineer models, extract private data, clone intellectual property, or exhaust resources |

**Exam Tip:**
- **Training phase attacks** target data and model integrity **upstream**.
- **Inference phase attacks** exploit model reasoning and boundaries **during live querying**.
- **Deployment phase attacks** target data confidentiality, intellectual property, and system availability.

---

## 4.3 Human Oversight & Governance Framework

| Level | Scope & Focus | Primary Function | Example Use Case |
|-------|---------------|------------------|------------------|
| **Human-in-the-Loop (HITL)** | Transactional / Decision-level | Gates high-impact, critical, or irreversible actions behind human authorization | AI drafts an incident notification or ticket update, but requires a security analyst to approve sending/updating |
| **Human Oversight** | Systemic / Governance-level | Continually monitors aggregate metrics (accuracy, fairness, drift dashboards) and holds authority to suspend automated operations | Suspending an automated firewall rule engine when a sudden spike in false positives occurs after an update |
| **Human Validation** | Quality Assurance / Due Diligence | Independently samples model outputs against ground truth and conducts controlled adversarial tests | Periodically feeding verified benign and phishing emails to a classifier to uncover blind spots and maintain audit trails |

**Exam Tip:**
- **HITL** = Direct intervention on individual high-risk decisions (stops excessive agency).
- **Human Oversight** = System-wide monitoring and emergency suspension authority.
- **Human Validation** = Periodic sampling and adversarial stress-testing against ground truth.

---

## 4.4 Key AI Attack Vectors & Differentiators

### Poisoning, Backdoor, and Trojan Attacks

| Attack Type | Mechanism | Where Introduced | Observable Characteristic |
|-------------|-----------|------------------|---------------------------|
| **Data Poisoning** | Injects corrupted or malicious records into the training corpus | Training dataset collection | Distorts decision boundaries; causes overall or targeted classification degradation |
| **Backdoor Attack** | Embeds a hidden trigger (pattern, phrase, or visual artifact) via poisoned training data | Training phase | Model behaves normally on all clean data, but reliably triggers malicious output when the trigger is present (e.g., blue sticker on stop sign interpreted as 60 mph speed limit) |
| **Trojan Attack** | Embeds malicious code, files, or payload inside the AI model artifact or container | Supply chain / Build pipeline | Functions normally as an AI model, but covertly executes unauthorized actions in the background (e.g., exfiltrating data to an external C2 server) |

**Exam Tip:** A **Backdoor** manipulates the *learned mathematical weights* via poisoned data so a specific input trigger causes an unexpected output. A **Trojan** hides *actual executable code/malicious files* inside the model package or container to run background malicious processes.

---

### Model Privacy & Extraction Attacks

| Attack Type | Goal | Attacker Technique | Primary Compensating Controls |
|-------------|------|--------------------|-------------------------------|
| **Model Inversion** | Reconstructs sensitive training data records | Systematically queries model and analyzes output probabilities/distributions | Differential privacy, output filtering, rounding confidence scores, rate limiting |
| **Membership Inference** | Determines whether a specific target record was in the training dataset | Compares confidence scores and prediction variations against threshold margins | DP-SGD (gradient clipping + noise), preventing overfitting, restricting precision of confidence outputs |
| **Model Theft (Cloning)** | Duplicates or reverse-engineers proprietary model capabilities | Automated scraping via high-volume querying, or stealing model weights from CI/CD pipelines | Strict rate limits, model artifact encryption, **decoy/honeypot endpoints** to detect automated probing |

**Exam Tip:**
- **Model Inversion** = "Can I reconstruct what a patient record looks like from model outputs?"
- **Membership Inference** = "Was Alice's specific record used to train this model?"
- **Model Theft** = "Can I replicate the model's functionality or steal its weights?"

---

### Evasion, Output Handling, and Agency Attacks

| Threat | Definition & Risk | Compensating Controls |
|--------|-------------------|-----------------------|
| **Input Manipulation & Evasion** | Subtle, imperceptible perturbations added to inputs (audio, text, images) that fool model decision boundaries | Automated input integrity checks, acoustic/language statistical analysis, human approval for sensitive actions |
| **Output Integrity & Insecure Output Handling** | Downstream systems execute raw AI outputs without validation, leading to XSS, SSRF, or command execution | Treat all AI output as untrusted; enforce strict **Schema Validation** (JSON); allow-list downstream actions |
| **Excessive Agency** | Granting models/agents excessive permissions or unconstrained tool access | Principle of least privilege, sandboxed execution, narrow tool parameters, Human-in-the-Loop approval |
| **Chain of Thought (CoT) Manipulation** | Manipulating the intermediate reasoning steps of an LLM, causing hijacked execution or sensitive trace leakage | Protect CoT integrity, redact secrets from intermediate reasoning traces, isolate CoT from user-visible outputs |
| **Model Skewing (Data Drift)** | Production data diverges from training baseline; attackers may induce skew to cause predictable silent failures | Continuous drift monitoring, similarity scoring against trusted baselines, canary records, scheduled retraining |
| **Model Denial of Service (DoS)** | Overwhelming model compute resources through complex, nested, or oversized queries | Strict rate limits, token budgets, execution timeouts, max reasoning chain depth caps |

**Exam Tip:** **Chain of Thought (CoT)** reasoning is used by models to plan and use tools. If manipulated via prompt injection, subsequent reasoning steps are hijacked. Because CoT may contain raw API keys or internal data, intermediate reasoning must never be exposed or logged without redaction.

---

## 4.5 Compensating Controls Matrix

| Control Category | Specific Technique | Defensive Action |
|------------------|--------------------|------------------|
| **Input Controls** | Prompt Firewalls | Intercepts incoming queries using pattern matching, ML classifiers, and contextual filters to block injection and jailbreaks |
| **Input Controls** | Prompt Templates | Parameterizes user input into predefined slots, ensuring strict separation between user data and system instructions |
| **Output Controls** | Schema Validation | Rejects any model output that does not strictly adhere to predefined JSON schemas (fields, types, formats), stopping exfiltration and syntax-based injections |
| **Output Controls** | Model Guardrails | Real-time policy validators that filter or block unsafe, biased, or non-compliant content generated by the model |
| **Data Integrity** | Cryptographic Hashing & Lineage | Applies SHA-256 hashes, digital signatures, and immutable ledgers to verify data authenticity and detect poisoning |
| **Deception Defenses**| Decoy / Honeypot Endpoints | Exposes fake model endpoints or system prompts; triggers immediate security alerts when probed by automated scrapers |
| **Privacy Defenses** | Differential Privacy (DP) | Injects calibrated mathematical noise into datasets or training gradients (DP-SGD) to mask individual record presence |
| **Architectural Defenses** | Cross-Model Validation | Runs inputs through multiple independent models to flag divergent outputs and detect hallucinations |
| **Architectural Defenses** | Grounding Checks | Validates factual claims in generated outputs against authoritative reference knowledge sources |

**Exam Tip:** **Schema Validation** is one of the most effective compensating controls against prompt injection and data exfiltration. If the model's output deviates from the strict schema (e.g., attacker injects extra fields or commands), the output is automatically dropped.

---

## Quick Check

1. **What is the key difference between a Backdoor attack and a Trojan attack in AI systems?**
<details><summary>Answer</summary>

A **Backdoor attack** poisons training data so the model's learned weights trigger malicious behavior only when a specific input pattern/trigger is present. A **Trojan attack** embeds actual malicious code or executable files inside the model artifact or container itself (typically via a supply chain compromise) to execute covert background actions.
</details>

2. **How does Model Inversion differ from a Membership Inference attack?**
<details><summary>Answer</summary>

**Model Inversion** reconstructs or extracts sensitive features and training data records by analyzing model outputs. **Membership Inference** determines whether a specific, known individual's record was present in the training dataset by analyzing output confidence scores.
</details>

3. **What is the distinction between Human-in-the-Loop (HITL) and Human Oversight?**
<details><summary>Answer</summary>

**Human-in-the-Loop (HITL)** operates at the individual transaction level, requiring human sign-off before high-impact or irreversible actions execute. **Human Oversight** operates at the systemic governance level, monitoring aggregate operational trends, dashboards, and fairness metrics, with the authority to suspend automated operations during anomalies.
</details>

4. **Why is Schema Validation considered an effective defense against prompt injection and data exfiltration?**
<details><summary>Answer</summary>

Because prompt injection and exfiltration attacks almost always require adding extra instructions, unexpected fields, or altered data types. Strict schema validation automatically rejects any output that fails to match the predefined schema (e.g., JSON structure).
</details>

5. **How do Decoy or Honeypot endpoints help protect against Model Theft?**
<details><summary>Answer</summary>

They mimic legitimate API endpoints or system prompts. Since legitimate users have no reason to interact with them, any high-volume querying or automated scraping directed at these decoy endpoints immediately alerts defenders to active model-cloning attempts.
</details>

6. **What security risks are associated with Large Language Model Chain of Thought (CoT) reasoning?**
<details><summary>Answer</summary>

1. Manipulating early reasoning steps via prompt injection alters all subsequent decisions because the model uses prior reasoning as context.
2. Intermediate reasoning steps can accidentally expose sensitive data, retrieved internal context, or API keys if logged or displayed to users.
</details>

7. **What is the primary role of an AI Model Registry?**
<details><summary>Answer</summary>

It serves as an auditable system of record tracking versions of models, training datasets, configurations, and evaluation metrics, ensuring governance, accountability, provenance, and rollback capabilities.
</details>

8. **How does Adversarial Training enhance model resilience during the development phase?**
<details><summary>Answer</summary>

By intentionally injecting crafted adversarial samples into the training pipeline, forcing the model to learn robust decision boundaries that tolerate evasion and input manipulation attacks.
</details>

9. **What risk arises from Insecure Output Handling, and how is it mitigated?**
<details><summary>Answer</summary>

Downstream systems (e.g., ticketing, web browsers, databases) may execute unvalidated model output as trusted code, leading to XSS, SSRF, or command injection. It is mitigated by treating all AI outputs as untrusted, enforcing strict output sanitization/schema validation, and allow-listing executable actions.
</details>

10. **What techniques can be used to detect and prevent Hallucinations before outputs reach end users?**
<details><summary>Answer</summary>

Grounding checks (validating claims against trusted authoritative knowledge bases), cross-model validation (comparing outputs from independent models), and separating output generation from automated execution pipelines.
</details>

---

*Version: v1.0 | Chapter: 4 | Domain: Distinguishing AI-Related Threats and Compensating Controls*
