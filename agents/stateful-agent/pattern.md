# Stateful Agent — Pattern Definition

> **How this definition was developed:** See [conversation-log.md](conversation-log.md) for the full deliberation process — 5 rounds of adversarial refinement, 5 independent sub-agent naming evaluations, and convergence on final definition.

## Overview

A **Stateful Agent** is an AI agent whose behavior is path-dependent — materially shaped by durable state that persists beyond any single session. Unlike a stateless agent, which begins every invocation from an identical baseline, a stateful agent's present behavior is a product of its history.

**The defining test:** deleting the agent's accumulated state would materially alter its behavior in ways not recoverable from configuration alone.

## Three Composable Properties

Statefulness in AI agents is not a single property but a composition of three independent patterns. Each is meaningful on its own. Together, they produce a qualitatively distinct kind of agent.

### 1. Path-Dependent State

The agent's behavior is materially shaped by durable state from prior interactions — not just the current input. State includes conversation history, accumulated knowledge, task progress, user preferences, and environmental context. State persists beyond any single session, is retrieved through a mix of deterministic access (known files, structured queries) and probabilistic search (semantic retrieval), and is bounded and lossy in practice.

### 2. Autonomy

The agent acts independently between user interactions — monitoring systems, executing scheduled tasks, responding to events, and initiating work on its own timeline. It is not purely reactive. It has its own operational loop.

### 3. Persistent Identity

The agent maintains a declared, consistent identity tied to a continuous lineage of accumulated state. It is the same entity across sessions, restarts, and time — not a fresh instance.

## Subtypes by Composition

- **Session-stateful** (property 1 only) — Context within a single conversation. State dies with the session. Example: chatbot with conversation history.
- **Persistent-stateful** (properties 1 + 3) — Durable state and identity across sessions. Acts only when prompted. Example: personal assistant with long-term memory.
- **Autonomous-stateful** (properties 1 + 2 + 3) — The full composition. Durable state, persistent identity, independent action. Example: always-on ops agent (e.g. OpenClaw).

An agent with autonomy but no state (property 2 only) is not a stateful agent — it is a scheduled automation. An agent with state but no identity (property 1 only) is session-scoped and fungible.

## Stateless Agent (Contrast)

A **Stateless Agent** is an AI agent whose behavior is path-independent — determined entirely by the current input and configuration, with no access to state from prior interactions. Each invocation begins from an identical baseline. The agent may produce side effects and non-deterministic outputs, but its behavior is never influenced by its own history. It cannot be said to have lost anything if reset, because it retains nothing.

## Naming Considerations

The full composition (1 + 2 + 3) represents a genuinely new pattern in AI agent architecture. Several names have been proposed, each with different strengths:

### Sovereign Agent

Captures self-governance, authority, and endurance. Most memorable and evocative. However, collides with "Sovereign AI" (NVIDIA/national AI infrastructure), carries AI safety concerns (implies absence of oversight), and maps asymmetrically — strong on autonomy, weak on state and identity.

### Resident Agent

A resident *lives there* — persistent presence (identity), knows the neighborhood (state), acts while you're away (autonomy). Computing precedent in "memory-resident." Intelligence precedent in stationed operatives. Humble and precise — a resident lives in someone else's infrastructure, implying capability within boundaries. Does not overclaim. Strongest consensus across evaluations.

### Steward Agent

Manages a domain on behalf of an owner with delegated authority. Safety-aligned by construction — stewardship is human oversight by definition. Strong mapping to all three properties but slightly passive in connotation. Best choice where trust, accountability, and AI safety framing are priorities.

### Other Candidates Evaluated

- **Standing Agent** — always-deployed, military clean
- **Vigil Agent** — the agent that never sleeps; sharp and concise
- **Covenant Agent** — relational depth, bilateral commitment
- **Familiar Agent** — companion with its own identity; evocative but niche
- **Sentinel Agent** — monitoring focus; too narrow, collides with Microsoft Sentinel
- **Continuant Agent** — philosophically exact, practically obscure

## Recommendation

Use the three properties (State, Autonomy, Identity) as the canonical decomposition. They are the pattern — the name is a label.

For the full composition, choose based on context:

- **Resident Agent** — general-purpose, technically precise, no baggage
- **Steward Agent** — safety-conscious contexts, enterprise, regulatory environments
- **Sovereign Agent** — when gravitas matters more than caution

The community will converge on one. Until it does, define the properties and let the name follow.

## Key Design Considerations

- **State is bounded and lossy.** Memory decays, gets pruned, and is subject to retrieval failure. The definition must be honest about this.
- **Agency is bounded by configuration.** The agent exercises genuine selection (what to remember, how to act) within configured patterns — directed autonomy, not free will.
- **Identity is pragmatic.** A declared label bound to a lineage of state. Not a philosophical claim about consciousness.
- **The model is stateless.** Statefulness is a system-level property of the agent (model + framework + storage), not a model-level property. The mechanism is compositional — stateless computation over durable state. The statefulness is real. The mechanism is emergent.
- **Where state lives is the differentiator.** State in the prompt (ephemeral, user-managed) = stateless. State in durable storage (persistent, agent-accessible, session-independent) = stateful. The line is not about degree of memory — it is about whether state outlives the conversation.
