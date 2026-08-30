---
title: "Glossary & Conceptual Foundations"
description: Clear definitions of core concepts from systems theory, knowledge graphs, and software architecture used in Exocortex.
tags:
  - glossary
  - systems-thinking
  - cybernetics
  - architecture
  - knowledge-graphs
---

> *"Clear concepts are the foundation of effective thinking. When definitions drift into ambiguity, systems lose their clarity."*

Exocortex draws practical concepts from systems theory, cybernetics, information theory, and software architecture. This glossary defines these terms plainly, explains their conceptual roots, and outlines their concrete technical role within the system.

---

### 1. Vector Space & Embeddings
* **Conceptual Origin:** Linear algebra and natural language processing. Concepts, words, or documents are mapped as dense numerical coordinate vectors ($\mathbf{v} \in \mathbb{R}^d$) in a continuous geometric space, where distance correlates with semantic relationship.
* **Role in Exocortex:** Prompts, active graph nodes, and search queries are embedded using local embedding models (such as `bge-m3` in a 1024-dimensional space). This allows the system to find conceptually related notes even when phrasing differs.

---

### 2. Semantic Similarity & Telemetry
* **Conceptual Origin:** Vector geometry. The normalized dot product (cosine similarity) measures the directional alignment between two vectors on a scale from $-1.0$ to $+1.0$:
  $$\text{sim}(\mathbf{u}, \mathbf{v}) = \frac{\mathbf{u} \cdot \mathbf{v}}{\|\mathbf{u}\|_2 \, \|\mathbf{v}\|_2}$$
* **Role in Exocortex:** Used for two core mechanisms:
  1. *Retrieval:* Identifying the most relevant nodes in the knowledge graph for a given user prompt.
  2. *Runtime Telemetry:* Calculating the **Echo Score** ($\rho_{\text{echo}}$) between prompt and response to detect conversational mirroring, and measuring **Epistemic Lift** ($\Delta E$) to verify that responses actively ground themselves in active knowledge nodes.

---

> **Node Taxonomy in v1.5.0:** The Exocortex knowledge graph organizes domain memory into four clear, software-native entity types with canonical prefixes (`CST_`, `CNC_`, `RUL_`, `STA_`).

### 3. Constraints (`Constraint` / `CST_`)
* **Conceptual Origin:** Invariant design, constraint satisfaction, and Karl Popper’s criterion of demarcation (a robust system is defined by what it strictly prohibits).
* **Role in Exocortex:** Inviolable guardrails and negative boundaries (e.g., *Side Effect Isolation*, *Intellectual Honesty*, or seasonal culinary restrictions). Constraints are injected statically into the system prompt to prevent bad architecture and sycophantic agreement. The solution space inside these boundaries remains completely open.

---

### 4. Concepts (`Concept` / `CNC_`)
* **Conceptual Origin:** Domain modeling, ontology engineering, and axiomatic foundations.
* **Role in Exocortex:** Foundational domain definitions and core principles in the knowledge graph. These nodes anchor the model's reasoning in verified domain knowledge (e.g., *Single Responsibility Principle* in software design, or *Ingredient Purity* in regional cooking).

---

### 5. Rules (`Rule` / `RUL_`)
* **Conceptual Origin:** Expert systems, heuristics, and procedural refactoring patterns.
* **Role in Exocortex:** Concrete action guidelines and transformation heuristics stored in the graph (e.g., *Defensive Design*, extracting interfaces, or gentle cooking techniques). They define *how* principles are translated into practical execution.

---

### 6. States (`State` / `STA_`)
* **Conceptual Origin:** State machines, execution contexts, and task tracking.
* **Role in Exocortex:** Ephemeral graph nodes capturing active working contexts, temporary hypotheses, code review checkpoints, or session markers. Unlike permanent constraints or domain concepts, states are updated, archived, or pruned as workflows progress.

---

### 7. Second-Order Cybernetics & The Observer Effect
* **Conceptual Origin:** Heinz von Foerster and Margaret Mead. The study of circular, recursive systems where the observer is an active participant in the observed system rather than a detached outsider.
* **Role in Exocortex:** Recognizing that prompt phrasing directly biases and steers model output. Because standard language models naturally echo the user's implicit biases (*sycophancy*), Exocortex uses explicit constraints to provide an independent, critical perspective rather than an uncritical echo.

---

### 8. *Via Negativa* (Constraint-First Design)
* **Conceptual Origin:** Epistemology and engineering (Nassim Taleb, Karl Popper). Improving systems by removing defects, bloat, and invalid states, rather than adding more procedural instructions.
* **Role in Exocortex:** System prompts and graph topologies focus on what *not* to do (hard boundary walls), giving the model maximum creative freedom to explore valid solutions inside those boundaries without micro-managing its step-by-step reasoning.

---

### 9. Purpose vs. Computation (Human Intent & Machine Limits)
* **Conceptual Origin:** Philosophy of mind and cybernetics. The distinction between mechanical/algorithmic processing (efficient cause) and ultimate purpose, values, and intent (*telos*).
* **Role in Exocortex:** The fundamental division of responsibility between human and machine:
  * *Delegable:* Syntax checking, edge-case detection, graph retrieval, code refactoring options, and structural auditing.
  * *Non-Delegable:* Setting direction, evaluating trade-offs, making final decisions, aesthetic taste, and ethical responsibility.

---

### 10. Requisite Variety & Anti-Deskilling
* **Conceptual Origin:** W. Ross Ashby's *Law of Requisite Variety* ("Only variety can absorb variety"). An operator must maintain sufficient internal problem-solving capacity to understand and regulate the system they oversee.
* **Role in Exocortex:** Actively preventing cognitive atrophy (blind copy-pasting). The engine explains trade-offs, highlights architectural flaws, and encourages surgical, incremental edits rather than dumping opaque, unreviewed blocks of code.

---

### 11. Context Economy
* **Conceptual Origin:** Information theory and cognitive load management. The trade-off between massive context windows and signal-to-noise ratio.
* **Role in Exocortex:** Instead of passing entire chat histories into context, Exocortex uses hybrid retrieval (vector search + 1-hop graph traversal) to assemble compact, focused context frames ($< 400$ tokens). This keeps latency low, prevents attention degradation ("lost in the middle"), and enables sharp reasoning on local $12\text{B}$ parameter models.

---

### 12. Dynamic Graph Maintenance
* **Conceptual Origin:** Graph databases and dynamic knowledge management.
* **Role in Exocortex:** Managing memory explicitly via standardized MCP tool calls:
  * `exocortex_query_graph`: Retrieves active concepts and constraints.
  * `exocortex_create_node`: Autonomously adds and links new nodes in the NetworkX graph.
  * `exocortex_mutate_node`: Updates weights, recalibrates, or prunes obsolete nodes.
  All graph mutations synchronize in real time to an interactive Obsidian `.canvas` file.

