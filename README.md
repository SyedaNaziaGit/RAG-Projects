# RAG Projects

A collection of Retrieval-Augmented Generation (RAG) implementations, from the basics to self-correcting and agentic pipelines. Each project lives in its own repo and is linked here as a submodule.

## Self-RAG vs Corrective RAG vs Agentic RAG

All three improve on basic RAG (retrieve, then generate) by adding decision-making. They differ in *what* gets checked and *who* decides.

| | Self-RAG | Corrective RAG (CRAG) | Agentic RAG |
|---|---|---|---|
| **Core idea** | The model reflects on its own retrieval and output | A retrieval evaluator checks document quality and fixes bad retrieval | An agent plans and picks tools and steps to answer |
| **What is checked** | Whether to retrieve, whether docs are relevant, whether the answer is grounded and useful | Whether retrieved docs are correct, ambiguous, or incorrect | Whether the current information is enough, and what to do next |
| **When it intervenes** | Before, during, and after generation | Right after retrieval | Throughout, in a multi-step loop |
| **Fallback behavior** | Re-retrieves or regenerates | Rewrites the query and falls back to web search | Chooses another tool, rewrites the query, or breaks the task into sub-questions |
| **Main strength** | Reduces hallucination and unnecessary retrieval | Handles poor or irrelevant retrieval | Handles complex, multi-source, multi-step questions |
| **Trade-off** | Extra LLM calls for grading | Depends on the evaluator's accuracy | Highest latency and cost, hardest to control |

### Which one to use

- **Self-RAG** when answer faithfulness matters most and you want the system to skip retrieval when it isn't needed.
- **Corrective RAG** when your knowledge base is incomplete or noisy and you want a web-search safety net.
- **Agentic RAG** when questions need multiple tools, data sources, or reasoning steps.

> They are not mutually exclusive. Self-reflection and corrective loops are often building blocks inside a larger agentic system.

## Projects

| Project | What it covers | Stack |
|---|---|---|
| [AgenticRAG](https://github.com/SyedaNaziaGit/AgenticRAG) | Step-by-step notebooks that build up from a base RAG pipeline to a full agentic RAG system | Python, LangChain |
| [Self_RAG](https://github.com/SyedaNaziaGit/Self_RAG) | Self-reflective RAG, where the model critiques its own retrieval and answers. Includes step notebooks and a Streamlit app | LangGraph, Streamlit |
| [Corrective_RAG](https://github.com/SyedaNaziaGit/Corrective_RAG) | Corrective RAG (CRAG), which evaluates retrieved documents and corrects course when they are poor. Step notebooks (in progress) | LangGraph |

## Suggested Order

1. **AgenticRAG** to understand the fundamentals and how agents fit in.
2. **Self_RAG** to see self-reflection applied to retrieval.
3. **Corrective_RAG** to see retrieval evaluation and correction.

## Cloning

Clone with the submodules included:

```bash
git clone --recurse-submodules https://github.com/SyedaNaziaGit/RAG-Projects.git
```

If you already cloned without them:

```bash
git submodule update --init --recursive
```
---
