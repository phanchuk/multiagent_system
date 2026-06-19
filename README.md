# 🔎 Multi-Agent Deep Research System

An agentic AI workflow designed to automate complex research tasks through collaborative AI agents using n8n, LLMs, and external retrieval tools.

The project explores how multi-agent systems can decompose ambiguous user requests into structured research activities, coordinate specialized agents, and generate high-quality reports with minimal human intervention.

---

## 💡 Description & Goal

Conducting comprehensive research is often time-consuming, inconsistent, and difficult to scale.

The goal of this project was to design and orchestrate a reusable multi-agent research system that:

* transforms vague user requests into clear research objectives,
* distributes work across specialized AI agents,
* automates web discovery and evidence gathering,
* synthesizes findings into executive-ready reports,
* explores the trade-offs between autonomy, quality, cost, and operational complexity.

---

## 💡 Key Features

* Native n8n form-based user experience
* User intent clarification through a dedicated support agent
* Multi-agent architecture with clearly separated responsibilities
* Parallel execution of research subagents
* Iterative research loops with reflection capabilities
* Web discovery using Brave Search
* Website extraction and summarization workflows
* Structured JSON outputs between agents
* Automated markdown report generation
* PDF report creation and storage in Google Drive
* Short-term memory for conversational continuity
* Experimentation with different LLM models through OpenRouter

---

## 🛠 Tech Stack

* n8n (workflow orchestration)
* OpenRouter (LLM gateway)
* OpenAI GPT-4.1
* OpenAI GPT-4.1 Mini
* Google Gemini 2.5 Flash Lite
* Brave Search API
* Google Drive API
* Markdown → PDF conversion
* JSON structured outputs
* JavaScript transformation nodes
* Hostinger (hosting, Docker)

---

## ⚙️ System Architecture (High-Level)

### 1. User Intake & Clarification

The workflow begins with native n8n forms that collect a research request.

A dedicated **Intent Clarification Agent** validates whether the scope is sufficiently defined.

The agent can:

* ask clarifying questions,
* maintain short-term conversational memory,
* structure responses as JSON,
* determine whether research can proceed.

---

### 2. Lead Orchestrator Agent

Once the request is validated, a **Lead Orchestrator Agent** coordinates the research process.

Its responsibilities include:

* defining the overall research context,
* decomposing the problem into research tasks,
* assigning work to Search Subagents,
* reflecting on research completeness,
* initiating additional research iterations when necessary,
* consolidating findings for downstream processing.

This architecture emphasizes clear separation of concerns rather than relying on a single monolithic agent.

---

### 3. Search Subagents

Specialized **Search Subagents** execute focused research tasks in parallel.

Each subagent:

* receives the broader research context,
* conducts Brave Search queries,
* selects relevant sources,
* invokes website extraction workflows,
* reflects on research progress,
* repeats discovery when additional evidence is required,
* returns structured findings to the orchestrator.

This approach balances breadth and depth while reducing bottlenecks.

---

### 4. Website Extraction Pipeline

A dedicated extraction workflow enriches research quality by analyzing selected sources.

The pipeline:

* retrieves website content through ScrapingAnt,
* summarizes findings using LLM chains,
* extracts facts and insights relevant to the assigned topic,
* formats outputs consistently in markdown.

The separation of extraction from search enables reuse and independent optimization.

---

### 5. Report Generation

A **Copywriter Agent** transforms fragmented findings into a coherent research document.

Responsibilities include:

* generating executive-ready reports,
* organizing content logically,
* preserving supporting evidence and links,
* producing structured markdown outputs,
* validating formatting quality through reflection loops.

The final deliverable prioritizes readability and completeness.

---

### 6. Document Delivery

Generated reports are automatically converted into PDF documents and distributed.

The workflow supports:

* Markdown-to-PDF conversion,
* HTML transformation,
* automated file generation,
* storage in Google Drive,
* asynchronous delivery to users.

---

## 🧠 Product Thinking

* Designed around **specialization over generalization**, assigning distinct responsibilities to individual agents.
* Uses **human-in-the-loop clarification** to improve research quality before execution.
* Explores **autonomy versus reliability trade-offs**, allowing agents to reflect and iterate without losing control.
* Optimizes for **scalability through parallelization**, reducing time-to-insight for complex topics.
* Employs **structured outputs** to improve orchestration robustness and reduce workflow failures.
* Considers **operational economics**, including API usage patterns and model selection trade-offs.

---

## 📸 Screenshots

### All Agents 
<img width="1043" height="627" alt="Deep Research Agents 1" src="https://github.com/user-attachments/assets/22ab96a2-4ff6-49c0-a317-f5227b4cdf1c" />

---
### User Intent Clarification
<img width="1099" height="533" alt="Deep Research Agents 2 - Intent" src="https://github.com/user-attachments/assets/586f58cd-3b3f-4a69-b765-9aa7c8583b61" />

---

### Lead Orchestrator Agent

<img width="623" height="540" alt="Deep Research Agents 3 - Orchestrator" src="https://github.com/user-attachments/assets/34a46f33-9f1f-4eb6-855d-82a5084ea2e7" />

---

### Search Subagent Architecture

<img width="1756" height="640" alt="Deep Research Agents 5 - Search Subagent" src="https://github.com/user-attachments/assets/178db6b8-08de-4403-a55b-312b5e1119fc" />

---

### Final Report Generation

<img width="805" height="537" alt="Deep Research Agents 4 - Copywriter" src="https://github.com/user-attachments/assets/1c266ad5-6b15-418d-a4b3-b17eadec0791" />
<img width="1134" height="675" alt="Deep Research Code" src="https://github.com/user-attachments/assets/dfd5444b-65a8-4ef5-9ea1-e8ca88234be0" />

---

### Final Report 

<img width="1849" height="898" alt="Deep Research Outputs" src="https://github.com/user-attachments/assets/b0d76433-db35-4889-aa2a-9053056320d4" />

---

## 📌 Notes

This project focuses on practical implementation of multi-agent systems from a Product Manager perspective.

The emphasis is not only on building AI workflows, but also on designing effective collaboration patterns between agents, defining boundaries of autonomy, and understanding the operational trade-offs required to move from experimentation toward production-ready AI systems.
