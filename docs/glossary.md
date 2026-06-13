# Glossary

Terms used across the Agentic Resource Discovery (ARD) specification and this site.

**Agentic resource** — Any external capability an AI client can call on to perform a task: an agent, MCP server, Skill, API, workflow, AI Catalog entry, or similar. The umbrella term ARD is built around.

**Agent Finder** — A *product*: one discovery service built on ARD. It is not the protocol itself — many discovery services, named or not, can implement ARD.

**AI Catalog (`ai-catalog.json`)** — The base, artifact-agnostic manifest standard ARD builds on. A publisher hosts an `ai-catalog.json` file describing its agentic resources. See the [AI Catalog Standard](ai_catalog_spec.md).

**AI client (client)** — An orchestrator, agent, or harness — a chatbot, IDE assistant, or automation — that discovers agentic resources through ARD and invokes the ones it selects over their native protocols.

**ARD (Agentic Resource Discovery)** — The open protocol defined by this specification: how agentic resources describe themselves, how clients ask for them, and how discovery services answer — all *before* invocation.

**Attestation** — A verifiable claim attached to a catalog entry's `trustManifest` (e.g. SOC2, HIPAA, GDPR) that a registry or client can fetch and check.

**Capability manifest** — Another name for the `ai-catalog.json` file a publisher hosts to advertise its agentic resources.

**Catalog entry** — A single agentic resource description within a manifest: its identifier, type, location (`url` or inline `data`), and optional metadata.

**Discovery service** — A service that indexes agentic resources and answers search queries (`POST /search`). The specification's formal term is **Agent Registry** (or **registry**); this site uses "discovery service" and "registry" interchangeably. **Agent Finder** is one such product.

**Federation** — How discovery services draw on each other. A search's `federation` parameter is `auto` (the service merges upstream results), `referrals` (it returns other services for the client to query itself), or `none`.

**MCP, A2A, Skill** — Examples of the execution protocols and resource types ARD wraps: Model Context Protocol servers, Agent-to-Agent agent cards, and Skills. ARD discovers them; each is invoked over its own protocol.

**Media type** — The IANA media type in a catalog entry's `type` field, identifying what an artifact is — e.g. `application/mcp-server+json`, `application/a2a-agent-card+json`, `application/ai-skill`. ARD acts as an envelope over these.

**Publisher** — Whoever hosts an `ai-catalog.json` describing one or more agentic resources, typically at `https://<domain>/.well-known/ai-catalog.json`.

**Referral** — An entry in a search response pointing to another discovery service the client may query itself (used with `federation: "referrals"`).

**Registry / Agent Registry** — The specification's term for a discovery service that exposes the standard REST search interface. See **Discovery service**.

**Relevance score** — The `score` (0–100) on a search result: a semantic relevance ranking from the discovery service. It is **not** a trust, compliance, or safety rating.

**Representative queries** — Sample natural-language queries (`representativeQueries`, 2–5 per entry) that registries use to build semantic search ranking.

**Trust manifest (`trustManifest`)** — Optional verifiable identity and trust metadata on a catalog entry: a cryptographic `identity` (e.g. `did:web`, SPIFFE), `attestations`, `provenance`, and a detached signature. ARD communicates these signals; it does not itself confer trust.

**URN identifier (`urn:ai:…`)** — A catalog entry's domain-anchored logical identifier, `urn:ai:<publisher>:<namespace>:<agent-name>`, where `<publisher>` is a verifiable domain. It roots identity in DNS and stays stable as infrastructure changes.

**Well-known URI** — The conventional manifest location, `https://<domain>/.well-known/ai-catalog.json`, where discovery services look for a publisher's catalog.
