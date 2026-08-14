<div align="center">

[English](README.md) | [中文](README.zh.md)

</div>

<div align="center">

# Cold Trust Protocol Stack

### Trust Protocols for Human–AI Interaction — a Computational Social Science Research Portfolio

</div>

<div align="center">

[![arXiv](https://img.shields.io/badge/arXiv-2512.08740-brightgreen.svg)](https://arxiv.org/abs/2512.08740)
[![DOI](https://img.shields.io/badge/DOI-10.48550/arXiv.2512.08740-brightgreen.svg)](https://doi.org/10.48550/arXiv.2512.08740)
[![figshare](https://img.shields.io/badge/figshare-31696846-blueviolet.svg?logo=figshare&logoColor=white)](https://doi.org/10.6084/m9.figshare.31696846)
[![Field](https://img.shields.io/badge/Field-CSS%20%7C%20HCI%20%7C%20AI%20Governance-6f42c1.svg)](https://github.com/cold-os)
[![Python](https://img.shields.io/badge/Python-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
![Status](https://img.shields.io/badge/Status-Pre--Alpha%20Research%20Prototypes-orange)

</div>

> **⚠️ Experimental Research Prototypes**
> The Cold Trust Protocol Stack is an open-source research portfolio initiated and maintained independently by an undergraduate computer science student. It explores one question: **how can humans and AI agents interact under auditable, verifiable terms of trust?** All six artifacts are early prototypes (proof-of-concept / pre-alpha) and **not suitable for any production environment**.

---

## 🧊 What Is This?

**One question, six artifacts.**

The Cold Trust Protocol Stack (CTPS) treats human–AI interaction as a *protocol problem*: what an agent may claim, what it may do, how claims are checked against actions, how authority is granted and audited, and how all of this is made visible to the human on the other side of the screen.

Instead of trusting the model's internal state, CTPS asks: **what agreements can we write down, verify, and show to a human?** Each layer of the stack answers one sub-question of that larger question — and each sub-question is implemented as an independent, runnable, open-source prototype.

It is a research portfolio at the intersection of **human–computer interaction, cognitive science, and AI governance**: the artifacts below exist to be *seen, studied, and critiqued* by people, not to be deployed.

```mermaid
flowchart TD
    subgraph L1[Cognition]
        A[ColdCognition\nbelief triples · adversarial dialogue]
    end
    subgraph L2[Contract]
        B[ColdContract\nZ3-encoded interaction contracts]
    end
    subgraph L3[Verification]
        C[ColdReasoner\nruntime consistency kernel]
    end
    subgraph L4[Governance]
        D[ColdTriad\npropose · review · execute]
    end
    subgraph L5[Runtime]
        E[ColdRuntime\ntokenized execution · audit trail]
    end
    subgraph L6[Interface]
        F[ColdLens\ntransparency dashboard]
    end
    A --> B --> C --> D --> E --> F
```

## 🎯 Why a Protocol Stack?

Mainstream AI-safety work tries to make the model trustworthy. CTPS takes the complementary position that emerged from the *dual black box* problem: **human expert intuition and AI decision-making are both opaque**, so the reliable surface between them is not a better model — it is a better *interaction protocol*.

Three commitments drive the stack:

- **Trust by architecture.** Trustworthiness is treated as a structural property, not a model property: unsafe actions should be *structurally impossible*, not merely discouraged. (See L4, L5.)
- **Auditability as a first-class feature.** Every decision is a replayable trace: who asked, what was claimed, what was checked, what was executed. (See L3, L5.)
- **Cognition-aware interaction.** Protocols must respect how humans actually form beliefs and calibrate trust — certainty is expressed in triples (certain / speculative / unknown), not in silent confidence. (See L1.)

## 📦 The Six Layers

| Layer | Artifact | Core Research Question | Current Status |
|-------|----------|------------------------|----------------|
| **L1 · Cognition** | [ColdCognition](https://github.com/cold-os/ColdCognition)  | How should an agent *express* what it believes vs. what it merely speculates? | Pre-alpha prototype |
| **L2 · Contract** | [ColdContract](https://github.com/cold-os/ColdContract)  | How can the terms of interaction be made formally checkable? | Pre-alpha prototype |
| **L3 · Verification** | [ColdReasoner](https://github.com/cold-os/ColdReasoner) | How can an agent's words be checked against its actions at runtime? | Pre-alpha, flagship |
| **L4 · Governance** | [ColdTriad](https://github.com/cold-os/ColdTriad)  | How can unsafe actions be made *structurally* impossible? | Pre-alpha prototype |
| **L5 · Runtime** | [ColdRuntime](https://github.com/cold-os/ColdRuntime)  | What does a full protocol-aware agent runtime look like? | Pre-alpha prototype |
| **L6 · Interface** | [ColdLens](https://github.com/cold-os/ColdLens)  | How do humans perceive and trust an agent operating under protocol? | Pre-alpha prototype |

### Layer summaries

- **L1 · ColdCognition** — RAMTN recursive adversarial dialogue (construct · challenge · observe) over three belief classes (*certain / speculative / unknown*), with Prolog-based consistency checking. *Question: can structured dialogue make an agent's epistemic state legible?*
- **L2 · ColdContract** — A minimal Z3-based encoding of the *belief–token–action* loop: what may be claimed, what may be done, and what follows from the claim. *Question: can interaction terms become decidable constraints?*
- **L3 · ColdReasoner** — The core consistency kernel: belief legality, action self-consistency, and behavior–belief consistency. *Question: can runtime verification outsource trust from the model to the protocol?*
- **L4 · ColdTriad** — Separation of powers for agents: a proposer that cannot execute, a deterministic reviewer that cannot act, an executor that only runs approved actions — default-deny. *Question: can unsafe actions be made structurally impossible?*
- **L5 · ColdRuntime** — An integrated FastAPI runtime: planning → pre-verification → one-time authorization token → execution → six post-checks (incl. content integrity) → tamper-evident dual audit (SQLite + JSONL). *Question: what does a full protocol-aware runtime look like?*
- **L6 · ColdLens** — A real-time transparency dashboard: belief-drift trends, radar charts, risk scores — the protocol made visible to the human. *Question: does seeing the protocol change how humans trust the agent? (planned user studies)*

## 🧪 Status & Limitations

**Honest state:** every artifact is a pre-alpha or proof-of-concept prototype, written in Python, largely AI-assisted in implementation, with core ideas and architecture authored by a single undergraduate. Explicit limitations:

- **No user studies yet.** The stack's central claims are about *human* trust and understanding — L6 exists but has not been run through systematic studies.
- No rigorous formal guarantees: L2/L3 encode decidable constraints but are not machine-checked proofs.
- Rule bases cover demo-level scenarios only; adversarial testing is incomplete.
- Isolation and token mechanisms are simulated, not production-grade.
- Not validated against real users.

**The author does not recommend any institution or individual use these artifacts in production, safety-critical, or real-world decision-making contexts.**

## 🗺️ For Reviewers: How to Read This Portfolio

- **Human-facing story first**: open [ColdLens](https://github.com/cold-os/ColdLens) and run the Streamlit demo — see what a protocol looks like to a person.
- **The core idea**: [ColdReasoner](https://github.com/cold-os/ColdReasoner) — the consistency kernel that makes "trust" a checkable property.
- **The governance idea**: [ColdTriad](https://github.com/cold-os/ColdTriad) — separation of powers applied to agents.
- **The theory**: the two papers below (RAMTN / Cold Existence) frame why protocols, not models, are the trustworthy surface.
- All repos run in minutes: `pip install -r requirements.txt` + a model API key (see each README).

## 🛣️ Roadmap

1. **Empirical validation (HCI)**: user studies on ColdLens — trust calibration, reliance, mental models.
2. **Adversarial evaluation** of ColdContract / ColdReasoner rule bases on real dialogue corpora.
3. **Integration** with mainstream agent frameworks (e.g., LangChain) as pluggable middleware.

## 📚 Papers

- Lu, Y. (2025). *Deconstructing the Dual Black Box: A Plug-and-Play Cognitive Framework for Human-AI Collaborative Enhancement and Its Implications for AI Governance.* arXiv:2512.08740. [https://doi.org/10.48550/arXiv.2512.08740](https://doi.org/10.48550/arXiv.2512.08740)
- Lu, Y. (2026). *The Cold Existence Model: A Fact-based Ontological Framework for AI.* figshare. [https://doi.org/10.6084/m9.figshare.31696846](https://doi.org/10.6084/m9.figshare.31696846)

## 🤝 Participation

This is an open, transparent, non-commercial academic exploration. The author welcomes critiques of architecture, code, and documentation; suggestions on verification rules and visualization; and interdisciplinary collaboration. Contact via Issues / Discussions in each repository. Contributors are acknowledged in the `CONTRIBUTORS` file.

## 📄 License

All code repositories are licensed under **Apache 2.0**. The core design documents and preprint papers retain the author's right of authorship; academic citation is permitted and welcomed.

## ✍️ Author

Initiated and maintained independently by an undergraduate computer science student working without a lab or advisor — as a sustained, self-directed research program. The author is fully aware of his limits; expert criticism is earnestly invited. Special thanks to the open-source community.

## 🕒 Research Timeline (selected)

- **2025.11** — Discovered that the independently-developed RAMTN prototype was highly similar in architecture to DeepSeekMath-V2 (open-sourced 2025.11.27); open-sourced RAMTN immediately.
- **2025.12** — *Meta-interaction* paper released on arXiv; ProdSim+ created as an initial RAMTN application.
- **2026.03** — *Cold Existence* paper rejected by three preprint platforms (category mismatch); published on figshare with a DOI.
- **2026.03–04** — CEAL, CAGE, ColdMirror, ColdReasoner, AtomTolopo, MetaSymbion and the ColdOS organization created — the stack takes shape.
- **2026.07** — BehaviOS: the integrated protocol-aware runtime.
- **2026.08** — The stack is re-organized and re-named as the **Cold Trust Protocol Stack**, positioned as an HCI / AI-governance research portfolio.

*— To be continued —*

---

**The Cold Trust Protocol Stack is an early-stage research portfolio on trust protocols for human–AI interaction.** It is not ready for production, but the question it asks — *what must a human and an agent agree on, before the agent acts?* — deserves careful, interdisciplinary exploration. Researchers in HCI, cognitive science, and AI governance are warmly invited to build on, criticize, or collaborate with this work.
