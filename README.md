# SecAI+

## Chapter 1 - AI & Data Concepts for Cybersecurity

### Core AI Concepts

Use a transformer-based model to process textual data, identify suspicious patterns in logs and emails, and extract relevant entities and relationships from threat reports.

Deep learning involves complex data preprocessing, data cleaning and transformation, feature engineering, and extensive tuning of neural network models before they can be deployed effectively. It requires extensive data preparation (cleaning, transforming, feature engineering, balancing) and understanding architectures, optimization, hyperparameter tuning, and deployment, making it more involved than simple Python analysis.

Transformers enhance the analysis of security-related text, such as phishing emails or incident reports, compared with simpler text-processing techniques, as they focus on the order and contextual relationships between words, allowing more accurate interpretation of intent and suspicious patterns.

Train an Isolation Forest model on the unlabeled login feature data to learn normal behavior, then score new logins and escalate those with the highest anomaly scores for analyst review.

Neural network architectures that focus on relationships within sequences of data is the correct answer. Transformers are neural network architectures that excel at processing sequences by modeling how elements (like words) relate to each other.

Generative AI refers to AI models that can generate new content by learning from large datasets of existing data, such as text, images, or code.

A key cybersecurity use of NLP is analyzing and categorizing large volumes of unstructured text such as threat reports, logs, chat messages, and emails. NLP is used to process unstructured text (logs, threat reports, chat messages, emails) for tasks like categorizing threat intelligence and extracting indicators of compromise.

Deep learning detects previously unseen or complex threats by learning from historical data. Traditional IDS detect known attacks using signatures and heuristics, while deep learning learns patterns from past data to identify novel or highly complex threats. This makes deep learning a powerful complement to IDS.

Statistical learning develops mathematical models to explain and predict data behavior, which directly supports anomaly detection and predictive analytics in cybersecurity.

On the offensive side, malicious threat actor groups may use generative AI to create highly realistic phishing simulations, craft malware samples with unique signatures, generate polymorphic code to evade detection, and automate the creation of deceptive content. Security professionals can use generative AI to enhance their defenses by creating threat scenarios, simulating attacks for red team exercises, and preparing their organizations to recognize and counter emerging generative threats.

Machine learning (ML) is a branch of AI that involves teaching computers to learn from data, identify patterns, and make decisions with minimal human intervention. Unlike traditional AI approaches that rely on explicitly programmed rules, Machine Learning systems automatically improve their performance via exposure to training data. Popular applications of ML include spam detection, recommendation systems, and image recognition.

Supervised learning involves training a model on a labeled dataset, where each input is paired with a correct output (such as labeling emails as "spam" or "safe"), enabling high accuracy for tasks like phishing detection. Machine learning models trained using supervised learning may struggle when confronted with novel threats or attacks that were not included during their training phase. This is a significant risk considering that cyber threats are constantly evolving and attackers routinely devise new techniques to bypass existing security controls.

Supervised learning is best suited for tasks that are well-represented in historical data, whereas unsupervised learning excels at anomaly detection in dynamic, essentially undefined, scenarios. The strengths of supervised learning include precision and auditability, whereas unsupervised learning offers scalability and flexibility.

In an unsupervised anomaly-detection system using autoencoders, a high reconstruction error for a particular log event usually indicates that the event differs significantly from the normal patterns the autoencoder learned.

Training a supervised machine learning model using the historical labeled login data to classify future login attempts as malicious or benign is correct. The analyst has labeled data, ideal for supervised learning, which can model relationships among time, IP, device, and geolocation to predict malicious logins.

Security tools can ingest and process the model's output with fewer custom parsers and less brittle integration code is a correct answer. Consistent JSON fields let SIEM, SOAR, and ticketing tools use simple ingestion rules instead of ad hoc text parsing.

Alerts can be enriched, prioritized, and routed automatically because fields like source IP and risk score are predictable is a correct answer. A stable schema lets downstream pipelines attach threat‑intelligence data, sort by priority, and trigger playbooks based on specific keys, which speeds triage and response.

Isolation Forest is an unsupervised learning algorithm that excels at identifying anomalies in high-dimensional data (for datasets that have such a wide range of data, it becomes difficult to track them all or identify which data matters the most) by isolating observations that are far from the norm. Its ability to handle large datasets and its resilience to outliers (meaning it can effectively identify anomalies even in high-dimensional data sets) make it a compelling choice for detecting unusual activity in cybersecurity and other data-intensive contexts. In a practical cybersecurity setting, Isolation Forest can be applied to tasks such as detecting unusual patterns in login activity, monitoring file access logs for abnormal behavior, or analyzing network traffic to identify potential intrusion attempts. These applications can help security teams detect insider threats, unauthorized access, or malware activity. However, using Isolation Forest effectively requires thorough data preparation.

Transformers can improve User and Entity Behavior Analytics (UEBA) by analyzing sequences of user activity to indicate insider threats or compromised accounts. This capacity to understand context and event relationships makes transformers a vital technology for SOC analysts, threat hunters, and security researchers.

The DistilBERT model is a simple sentiment classification model that only produces the labels "negative" and "positive."

Deep learning, a subset of ML, uses multi-layered neural networks to learn complex patterns from data. It excels at processing unstructured and high-dimensional data, making it highly effective for tasks like image recognition, speech processing, and natural language understanding. In cybersecurity, deep learning is particularly valuable for analyzing large and complex datasets, such as logs and network traffic. It can help classify malware, detect advanced persistent threats (APTs), and support intrusion detection systems by identifying subtle patterns of behavior that may indicate an attack.

Large language models (LLMs), like OpenAI's GPT models, are highly capable and used extensively in complex tasks such as summarizing threat intelligence reports, generating security playbooks, and interacting with users via conversational security bots.

Small language models (SLMs) are lighter and faster, making them ideal for real-time monitoring tasks on limited resources, such as analyzing logs, identifying suspicious behavior, or quickly classifying security alerts. While they lack the extensive knowledge and capabilities of LLMs, SLMs are more efficient and can be integrated into security appliances or embedded systems where resources are limited. SLMs have much lower parameter counts than LLMs, ranging from a few million to the low-billion range. Architecturally, they are often optimized for efficiency, and their hardware requirements are modest compared to LLMs. Many SLMs run sufficiently well on "everyday" CPUs with modest amounts of RAM.

Generative adversarial networks (GANs) consist of two neural networks contesting each other, one generating synthetic data samples and another distinguishing real from fake. This competitive training process makes GANs especially powerful for generating realistic data.

GANs play a vital role in generating synthetic but realistic threat scenarios for training and testing security systems. For example, they can create synthetic logs that resemble real-world attack patterns, enabling the development of robust intrusion detection systems. GANs can also be used to generate new malware variants for red team exercises or to test the resilience of machine learning-based security models against adversarial attacks.

Model Validation is the process of testing a trained AI model on previously unseen data to evaluate how well it generalizes (accuracy, fairness, robustness, etc.) and to confirm that it meets the requirements before deployment.

Classic training approaches partition a data set into three mutually exclusive segments:

- The Training set — the data from which the algorithm learns patterns
- The Validation set — the data used for quality and sanity checks during development
- The Test set — data used to provide a final, unbiased performance estimate

A stronger check is called k‑fold cross‑validation, where the data is split into k equal parts (folds). The model is then trained k times, each time holding one fold out to test the model and using the other k − 1 folds to train it. When all k runs are finished, the average test score is taken. This average makes the evaluation less dependent on any single lucky or unlucky data split.

**Overfitting**: when a model memorizes its training data and fails to generalize.
**Concept drift**: when the kinds of real‑world data the model sees slowly change, for example, spammers adopting new keywords.
**Silent data‑poisoning attacks**: where adversaries subtly manipulate training data to embed hidden vulnerabilities.

Once these baseline checks are established, organizations can probe their resilience through controlled adversarial simulations (red‑team exercises). In a red‑team exercise, outliers and poisoned samples are injected into the validation set, replicating how an attacker might probe the model's blind spots. Tracking how performance shifts under these conditions reveals whether the system has become overconfident, brittle, or too fragile to handle even slight variations from its training data.

**Weak supervision**: This approach involves auto-tagging raw logs with indicators from threat intelligence feeds. While weak supervision speeds up data curation, it can also introduce label noise, leading to inaccurate or conflicting tags and systematic bias.

Mitigations include regular label audits (human spot-checks that compare auto-generated tags with expert assessments), confidence weighting (reducing the statistical influence of labels from lower-trust sources), and semi-supervised refinement loops (retraining the model on its own high-confidence predictions that analysts have verified).

**Logistic Regression for Intrusion Detection — Five logical stages:**

1. **Collect & label**: Label each record as either benign (normal traffic) or malicious (potentially harmful activity).
2. **Pre‑process**: Clean and prepare the data.
3. **Split**: Set aside 20% of the data as a validation set.
4. **Train**: Build a simple model called logistic regression.
5. **Evaluate**: Check how well the model performs by calculating metrics such as precision (how many flagged items were actually malicious), recall (how many malicious items were correctly flagged), and F1 score (a balance of precision and recall). Review the confusion matrix, which shows where the model made correct and incorrect predictions, to understand the trade-offs between catching threats and avoiding excessive false alarms.

Autoencoders are small neural networks trained to recreate the records they see during learning.

Isolation Forests cut the data space at random. If a particular log line or network session can be separated from the bulk of the data after only a few cuts, the algorithm marks it as an outlier.

Unsupervised learning does not rely on prior labels or predefined attack patterns, so it can spot brand-new tactics and malware families just minutes after they appear, offering a crucial line of defense during zero-day attacks, insider threats, or cloud-service misuse that would otherwise go unnoticed.

Unsupervised detection acts as a backup safety net for traditional rule-based defenses. When attackers use novel techniques that slip past outdated or incomplete signature sets, anomaly detection can still trigger alerts, reducing attacker dwell time (the period during which a threat remains hidden inside the network and causes harm) by providing early warning of unusual behaviors such as unexpected data flows, rare administrative actions, or uncharacteristic login patterns. Each anomaly flagged by the system serves as a real-world case study. Once an analyst verifies and labels it, this record strengthens the training set, allowing future supervised models to learn from past incidents and recognize similar threats more quickly. This feedback loop steadily increases detection accuracy over time and helps organizations build adaptive defenses that keep pace with evolving adversaries.

Where supervised and unsupervised models stop at detection, reinforcement learning (RL) extends capabilities to include response.

- **State** (What the agent sees): At each step, the agent ingests a compact snapshot of its environment, for example, protocol, byte count, historical alert level, and current activity related to firewall rules.
- **Action** (What the agent can do): Options might include allow, throttle to 100 kbps, drop, or isolate host.
- **Reward** (How the agent is scored): A blocked confirmed malware sample might earn +10, a false positive incurs -3, and added latency -1.

This cycle — state → action → reward — repeats thousands of times in a test lab that replays recorded network traffic, as an example. After each round, the agent fine‑tunes its policy. A policy is simply a compact lookup table or neural‑network file that links every observed situation to the action most likely to maximize long‑term security while simultaneously minimizing user impact. Training stops when the running average of rewards levels off, indicating the agent is no longer simply guessing but has learned an effective and stable strategy. The new policy is then exported (often only a few megabytes and saved in one of several different formats) and deployed in shadow mode. In this phase, the agent does not enforce its choices; it merely posts recommendations alongside the actions taken by human analysts. If, after one or two weeks of side‑by‑side comparison, the agent's advice consistently matches or outperforms human decisions, the organization can confidently switch to autonomous mode, allowing the agent to act on its own while still logging every decision for audit and rollback.

Increase the reward for quickly blocking traffic later confirmed malicious and raise the penalty for prolonged throttling that causes latency, then retrain the agent on the same replayed traffic.

Fine-tuning is an essential technique in machine learning that builds on the concept of transfer learning. It involves taking a neural network model that has undergone extensive training on a large and diverse dataset, referred to as pre-training. To enhance the model's effectiveness for a specific task (such as identifying malicious user activity), fine-tuning is performed using a smaller dataset tailored for that purpose. This additional training allows the model to become more specialized while benefiting from the broad knowledge acquired during pre-training.

Pre-training is training a large model from scratch (or near-scratch) on a massive, general dataset to learn broad patterns like language, code, image features and cybersecurity knowledge from static data, creating a strong base that RL later fine-tunes for specific, reward-driven defensive (and safety-constrained) behaviors.

Retrieval-Augmented Generation (RAG) — no training required. The model retrieves relevant documents provided as inputs and uses them as context to generate answers to prompts, including how it decides when and how to use it.

Pruning is another important technique that complements fine-tuning. Pruning involves removing less important elements of the model, such as weights that have a negligible impact on performance. This process can occur either before or during fine-tuning, with the aim of reducing the model's size and improving inference speed, all while maintaining accuracy. Pruning is especially beneficial for deploying models in resource-constrained environments, such as mobile devices, where memory and processing power are limited.

Quantization serves as a key strategy for enhancing model efficiency. This technique involves altering how the model's weights and activations are represented. Instead of utilizing high-precision formats like 32-bit floating-point numbers, the model is converted to lower-precision formats, such as 8-bit integers. This conversion often takes place during or after the fine-tuning process, resulting in considerable memory savings and improved prediction speed. To preserve performance during this shift, techniques like quantization-aware training can be applied, helping to maintain the model's effectiveness.

While federated learning has many advantages over other learning models, there are some unique challenges it presents.

One of the main challenges of federated learning is device heterogeneity. The decentralized manner of federated learning can mitigate bias, but the challenge is that different devices may have more data than others and leads to a balancing issue. Devices with more data will skew the learning to those data-heavy devices, which can lead to model drift. While traffic is reduced compared to centralized data transfer, federated learning does still require a lot of communication between devices. If there is a large number of client devices or an unstable network, this can create issues with low bandwidth, latency, training time, and scalability. Federated learning is susceptible to data poisoning attacks. Secure aggregation is when all user's data is encrypted and then sent to the server. The server decrypts the data only when enough updates are combined, revealing only the average of all updates. The server never sees a single user's data. Differential privacy is another technique that can be used to help protect the privacy of users. Differential privacy adds carefully calibrated noise to all user's data so that each individual's contribution is hidden, but the overall results stay useful and accurate.

### Prompt Engineering

While the system role sets the outer guardrails, the user prompt is the steering wheel that directs the model toward a specific analytic goal. Designing an effective prompt means blending three elements in a single, concise instruction: context (the evidence the model will inspect), perspective (the analytical lens or persona it should adopt), and output shape (the exact format required by downstream tools).

**Zero-shot prompt**: An AI prompting technique where the model is asked to perform a task with no prior examples in the prompt, only an instruction or description, relying entirely on its pretrained knowledge to infer how to complete the task.

**One-shot prompt**: An AI prompting technique where one example input‑output pair is included in the prompt before the real query so the model can learn the desired format or behavior from that example and apply it to the new request.

**Multi-shot prompt**: An AI prompting technique where several example input‑output pairs are provided in the prompt before the real query so the model can infer the desired pattern, style, or task from those multiple examples and apply it to the new input.

Prompt templates give language models the same operational discipline by ensuring their outputs follow a repeatable, standardized structure. This means the model's responses will consistently include the right fields, formats, and terminology required by security teams and automated tools, making integration into cybersecurity workflows easier for both beginners and experienced professionals.

**Policy filters embedded in the system prompt**: Add a sentence such as, "Reject any request to produce shell commands unless the user_role variable equals admin." This prevents privilege escalation even if an attacker gains interactive access.

**Guardrail frameworks**: Tools such as OpenAI Guardrails or Nvidia NeMo Guardrails act as protective layers that sit between the user's input and the model's final output. They inspect both the prompt and the model's draft response, checking them against rules such as JSON schemas (which define the exact structure of acceptable outputs) or regular-expression allow-lists, which specify safe patterns. By performing these checks, the guardrails help ensure that only safe, properly formatted responses are returned to the caller, reducing the risk of unintended or harmful outputs.

**Watermarking and signed responses**: Cryptographic watermarks are hidden markers or codes added to the model's output that are difficult to forge or remove. These markers allow downstream systems and analysts, such as SIEM platforms that store and process security logs or cybersecurity professionals who review AI-generated reports.

**Rate-limiting and exhaustive audit logging**: Throttling requests at the API gateway (for example, setting a limit of 10 requests per minute for each API key) slows down brute‑force prompt probing attempts that try to guess instructions or bypass security filters. Meanwhile, detailed audit logs capture every request and response along with timestamps, user identifiers, and source IP addresses. This creates a forensic timeline that incident responders can review during investigations to trace suspicious activity, reconstruct attack chains, or demonstrate compliance during audits.

A practical starting point is to deploy OpenAI Guardrails as a reverse proxy, which means it sits between your application and the AI model to monitor and filter requests and responses.

### Data Security

Structured data plays a key role in traditional security analytics. This type of data includes firewall logs, NetFlow records, and indicators of compromise (IOC) lists, all of which are organized in specific formats that make them easier to analyze and us

Semi-structured data sources are types of data formats that combine elements of both structured and unstructured data. Common examples include JSON, email headers, and YAML.

Unstructured data includes things like packet payloads from network traffic, chat transcripts from analyst discussions, and images taken from security cameras.

Watermarking provides organizations with a mechanism by which the source of any information can be validated as necessary. By embedding invisible identifiers within AI-generated content (such as text, images, or audio), developers incorporate a verifiable trail that establishes the origin of the data. These protections are crucial for machine learning processes, as training datasets often contain sensitive or proprietary information.

In a legal context, watermarking protects organizations against infringement. By demonstrating a clear link between the data and its rightful owner, watermarking supports an organization's legal standing should disputes arise regarding content usage. In situations involving machine-generated outputs, the line between creativity and copyright infringement can be blurry, and watermarking can go a long way to support ownership claims.

Model watermarking adds another layer of security, specifically targeting the algorithms that drive AI systems. By embedding specific test prompts that produce repeatable and uniquely recognizable outputs, developers can safeguard their models from duplication or reverse engineering by competitors or other threat actors.

Retrieval‑augmented generation (RAG) addresses this problem by pushing fresh knowledge into vector storage (a lookup table that turns pieces of text into numeric fingerprints called embeddings) while keeping the foundation model (the large, general‑purpose AI system already trained on vast, diverse data) unchanged.

Some examples of protections designed to protect RAG data include encryption of the vector index (the database that stores those numeric fingerprints), tenant isolation to prevent one department from accidentally or deliberately viewing another's proprietary information, and sanitizing all questions and documents entering the system to block prompt‑injection attacks before they reach the model.

Attackers weaponize AI to automate reconnaissance, craft more convincing phishing campaigns, and probe defenses at machine speed.

### Data Handling Techniques

- **Data cleansing**: Removes duplicates, fills in missing values, and resolves contradictory entries, ensuring that downstream algorithms learn from accurate signals rather than irrelevant noise.
- **Data verification**: After cleansing, datasets undergo data verification to confirm that the information feeding a model is precisely what was initially approved. This step blocks data‑poisoning attempts that can skew model weights toward incorrect or biased outcomes. A reliable defense is to generate a cryptographic hash for every dataset ingested, then store the hashes in a trusted, read‑only location. Command-line tools like `sha256sum` on Linux or `Get-FileHash` in PowerShell make it easy to spot even the smallest changes. In automated build or data‑prep pipelines, a verification stage can recalculate hashes and fail the job if the value differs from the baseline.
- **Data lineage**: Records every transformation a dataset undergoes, while data provenance documents its origin, licensing, and consent terms.
- **Data integrity**: Safeguards ensure that data arrives at its destination exactly as it was sent from the source by implementing digital signatures. In highly regulated or multi‑party environments, teams often add an append‑only blockchain or distributed ledger layer. Each data batch is hashed, and the hash is written to the ledger along with a timestamp, creating an immutable audit trail that regulators and partners can inspect.
- **Data augmentation**: Intentionally generates additional training examples by rotating images, flipping text sequences, or adding noise (minor random variations) so that the model learns to generalize instead of memorizing.
- **Data balancing**: Techniques realign the training set so that rare yet critical events receive proportionate attention. Down‑sampling does the inverse, randomly discarding enough benign entries to match the minority count, preventing model bias toward the majority.

Behavioral analytics engines identify anomalous data flows, such as an unexpected spike in training set size that could signal a poisoning attempt, while natural language models inspect data catalog metadata for compliance violations.

## Chapter 2 - Implementing Threat Modeling and Securing AI Systems

AI threat modeling is a process of identifying potential threats and analyzing the risks associated with AI systems.

Attackers can jailbreak the AI models and perform data poisoning, which can lead to data integrity issues and spreading misinformation. Lack of rate limitation on the usage of AI leads to unlimited utilization of services, causing exhaustion of back-end resources, financial impact, and availability issues. Performing AI threat modeling in the early stages of Secure Software Development Life Cycle (SDLC) would help identify and prevent the risks associated with using AI in applications.

Some of the widely recognized and used AI threat resources are the Massachusetts Institute of Technology (MIT) AI Risk Repository, the Common Vulnerabilities and Exposures (CVE) system, the AI Vulnerability Database (AVID), the AI Incident Database (AIID), and arXiv.

MIT AI Risk Repository is one of the major sources of AI threats helping security personnel. The repository contains over 1,600 AI risks sourced from 65 existing frameworks, seven domains, and 24 subdomains. It includes the classification of AI risks into taxonomies on the basis of how, when, why, and in what domain the risks occurred. This repository is updated on a regular basis and acts as a live database.

MIT AI risk repository contains three parts:

- AI Risk database
- Causal Taxonomy of AI Risks - This taxonomy classifies risks based on how they are originated and whether a risk is caused by a decision or action made by AI, human user/developer, or other external factors. It distinguishes whether the risk is caused intentionally, like the expected outcomes of a goal, unintentionally, or even classified as "other", which can't be determined.
- Domain Taxonomy of AI Risks—The domain taxonomy classifies risks into seven AI risk domains and 23 subdomains, such as (1) Discrimination & Toxicity, (2) Privacy & Security, (3) Misinformation, (4) Malicious Actors & Misuse, (5) Human-Computer Interaction, (6) Socioeconomic & Environmental, and (7) AI System Safety, Failures, & Limitations.

CVE AI workgroup is part of the common vulnerability enumeration (CVE) program, which is a committee of members from within the board of CVE, corporate members who perform vulnerability management, members of the AI community, and their associations.This group would analyze and identify AI threats, assigning them a CVE ID and making them part of the CVE database.

AI Vulnerability Database (AVID) is an open-source knowledge base that collects data about failure modes for AI models, datasets, and systems. This database would provide a structured approach for security teams to identify, assess, and mitigate AI-specific vulnerabilities. Security teams or development teams, before deploying any AI component, can search AVID for known vulnerabilities that may affect the model, dataset, or application programming interface (API) they plan to use.

AI Incident Database is a collection of AI incidents that happened in real-time. The collection includes vast information from the Internet on everyday threats caused by AI systems, like deepfakes, biases, and misuse of AI. This database helps security teams and researchers to study these incidents; threat hunters can identify common attack patterns and vulnerabilities that may exist in their own systems.

arXiv is an open-source platform where researchers share scientific papers. It covers the research from different fields of study, including artificial intelligence (AI). Researchers around the world upload their latest findings to arXiv to share knowledge and get feedback from the community.

The Common Weakness Enumeration (CWE) is a widely used framework for identifying and categorizing software vulnerabilities. With respect to AI and model security, CWE can be adapted to map real-world threats to specific types of system weaknesses. For example, CWE-77 (Command Injection) is relevant for prompt injection attacks where user input manipulates model instructions. CWE-200 (Exposure of Sensitive Information) aligns with risks like system prompt leakage or model inversion. 

Create a list of all the AI frameworks available for performing threat modeling and choose the one that could fit the analysis of the current business use case of the application that will be developed. Some of the popular frameworks are given below:

Open Web Application Security Project (OWASP) Top 10

Large Language Model (LLM) Top 10

Machine Learning (ML) Security Top 10

MITRE Adversarial Threat Landscape for Artificial-Intelligence Systems (ATLAS)

AI Risk Management Framework (NIST)

Threat-modeling frameworks

STRIDE

DREAD

MAESTRO framework

Open Web Application Security Project (OWASP) Top 10

Prompt injection involves manipulating inputs sent to LLM to change the behavior of the LLM or to leak information. This vulnerability override system prompts or instructions. This threat occurs in when user prompts are parsed and merged with system-level instructions.

Sensitive information disclosure occurs when the model unintentionally reveals private or proprietary data, often due to being trained on datasets that contain confidential or internal information or lacking proper output filtering.

Supply chain vulnerabilities introduce risk, particularly when third-party models, datasets, or plugins are integrated without thorough security review and improper patch managements. These external components might have vulnerabilities with public exploits allowing attackers to infiltrate into downstream systems.

Allowing malicious actors to change model behavior through tampered training or fine-tuning data. This can enable a change in how the model interprets future inputs or output biases, or provides harmful content to users.

 Output Handling

Improper output handling arises when generated responses are used directly in applications—like automation scripts or Application Programming Interface (API) calls—without verification. Since model outputs can include unsafe commands or embedded code, this can lead to vulnerabilities like SSRF, XSS, remote code execution, etc.

Excessive Agency occurs when LLMs are granted access controls for tools, systems, or workflows. The misconfigurations or excessive permissions will allow the LLM to perform actions it wasn't meant to. This can lead to unauthorized tasks, misuse of privileges, or operational failures.

System Prompt Leakage: Attackers can manipulate the model into revealing system prompts or instructions. These instructions are responsible teaching the model how it must respond back to user. This often occurs due to a lack of segregation between user and system contexts. These prompts can be reverse-engineered to exploit the system further.

Vector and Embedding Weakness: This relates to how LLMs store and retrieve semantic information. Misconfigured embedding spaces can allow attackers to reconstruct sensitive content or manipulate search results by injecting malicious content.

 Misinformation

Misinformation: Hallucinations or biases that would impact decision-making of the user is another security risk. This occurs when outputs are not validated with reliable sources.

 Unbounded Consumption: Without strict rate limits or query filters, LLMs can be abused—intentionally or unintentionally—leading to uncontrollable consumption of backend services, which can impact the operational costs, or even denial of service.

 Machine Learning (ML) Top 10

 	
Input manipulation occurs when an attacker crafts a malicious input to exploit the model's behavior. It targets the decision phase, where even small changes to input can trigger incorrect predictions or bypass controls.

Data Poisoning Attack: A threat where attackers inject misinformation or malicious data into the training dataset. This occurs when data sources are not authenticated or validated. This leads to the model being trained on incorrect data, causing biased behavior, changes in performance, or creating backdoors that activate under certain conditions.

Model Inversion Attack: 	
An attacker reverse engineers the model to get the sensitive information it is trained on. This happens when the history is used for training the model, which will enable the model to save the data, which can have sensitive information.

 Membership Inference Attack: 	
An attacker trains the model with a specific set of records and uses it to inquire the particular data that was used in the model's training data set. This allows the attacker to gain access for sensitive information.

Model Theft: An attacker reverse engineers the organization's machine learning model to gain the access to training data and algorithm. Then the attacker clones the model and utilizes it for personal gain. This affects the proprietary model to causing finance loss and reputational damage to the organization.

AI Supply Chain Attack: Developing ML systems includes a different software bill of materials, which includes data and model management platforms, including open-source packages as well. The attackers might use the publicly available exploits to infiltrate the ML systems through the supply chain packages if not validated or patched properly.

Transfer Learning Attack: 	
When pre-trained models with inherited vulnerabilities are utilized for fine-tuning, this helps attackers to exploit the weakness and introduce malicious behavior. The pre-trained models can also have backdoors or biases if utilized without validation.

Model Skewing: The behavior of a machine learning model is altered through biased or manipulated training or feedback data. This happens when systems learn from the requests and responses it has worked on. This would result in the model behaving biased, or a change in the accuracy of the model.

Output Integrity Attack: 	An attacker tries to change or interfere with the final output of a machine learning model. If the access controls are improperly configured or invalidated, it can lead to tampering of output, which can share the misinformation back to the user and impact on decision-making.

 Model Poisoning: Model poisoning is a type of attack where harmful data or code is intentionally added during the model's training or fine-tuning process. It occurs when the attacker changes the model parameters without affecting its original performance. It can have high impact, especially in automated systems, as they may process harmful inputs and cause change in output without detection.

 MITRE Adversarial Threat Landscape for Artificial-Intelligence Systems (ATLAS) is a globally accessible framework developed to understand the various techniques and tactics adversaries use to attack AI and machine learning systems. It focuses on data poisoning and model evasion to imitate the extraction and misuse of AI functionality. It provides a structured knowledge base of attack scenarios, mapped tactics, and techniques during different phases of the life cycle.

 ATLAS helps security teams by offering a common language and clear guidance for identifying, analyzing, and mitigating AI-specific threats. Its key aspects include mapping attacks to each phase of the machine learning pipeline and categorizing adversarial goals (such as affecting model availability, integrity, or confidentiality).

 The NIST AI Risk Management Framework (AI RMF) is a structured guideline created to help organizations understand, evaluate, and manage risks associated with artificial intelligence systems. It focuses on promoting trustworthy and responsible AI by addressing concerns such as safety, security, fairness, privacy, explainability, and resilience. The framework is designed to be flexible and adaptable for a wide range of sectors and use cases, making it suitable for developers, operators, and decision-makers involved in AI systems.

 The framework outlines the challenges for AI risk management, like measurement, tolerance, prioritization, and management. It is built around four core functions: map, measure, manage, and govern. These functions guide teams through identifying where AI risks exist, measuring their potential impact, managing those risks with appropriate controls, and establishing governance processes for long-term oversight.