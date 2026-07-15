# Introduction

`Langchain` is a framework for building appliactions powered by `Large Language Models`

## Why Langchain

- Model abstractions for interfacing with Language models
- Prompt templates for designing and generating standard prompts
- Vector store adapters for storing and retrieving contextual information for prompts
- Tooling framework for working with external services
- and many more

---

| Without LangChain | With LangChain |
| :--- | :--- |
| Knowledge of each LLM provider's API you want to build with | Work with different LLM providers in a single project using one interface |
| Dealing with API changes of each LLM provider | LangChain keeps up with all the underlying API changes for each provider |
| Different workflows for tool calling, RAG, structured outputs, etc | Uniform workflows for tool calling, RAG, structured outputs, etc |
| Changing to a new provider requires a complete rewrite of your application | Easily swap LLM providers without changing your application's logic |

---

## EcoSystem

| Package / Tool | Description |
| :--- | :--- |
| **langchain-core** | Contains base abstractions for models, prompts, parsers, tools etc |
| **langchain** | Contains architecture tools like chains/workflows, agents, and retrieval strategies |
| **Integration Packages** | Packages for major LLM providers and integration tools e.g. `langchain-openai` (for OpenAI models), `langchain-chroma` (for Chroma Vector Store) |
| **langchain-community** | Third-party integrations by the LangChain community (not maintained by the LangChain team) |
| **langgraph** | Orchestration framework for building complex workflows and AI Agents |
| **langserve** | Helps in deploying your LangChain applications to production as REST APIs |
| **LangSmith** | An Observability platform for debugging, testing, evaluating and monitoring your LangChain/LangGraph applications |

---

## Langchain Components

- Chat Models
- Message Types
- Prompt Templates
- Output Parsers
- Document Loaders
- Text Splitters
- Embeddings
- Vector Stores
- Retreivers
- Tools
- Memory
- Agents

and many more
