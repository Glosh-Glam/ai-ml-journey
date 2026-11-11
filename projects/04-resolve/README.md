# Project 4: Resolve (Weeks 12–14)

**Brief:** A support agent that reads incoming tickets, screens them for prompt injection, searches the knowledge base, and proposes a resolution behind output guardrails.

## Deliverables
- [ ] Knowledge base indexed in OpenSearch (local Docker), and a RAG answer function with citations (W12)
- [ ] LangGraph ticket graph: classify → injection screen → retrieve → draft → guardrail → resolve/escalate (W13)
- [ ] MCP server exposing tools (ticket lookup/update, doc search) backed by a mock or a free Atlassian sandbox (W13)
- [ ] LangSmith tracing (W13)
- [ ] 30-question eval set with Ragas faithfulness and an LLM-as-a-judge score (W14)
- [ ] Red-team suite of 20+ injection/jailbreak cases run in CI, plus `THREAT_MODEL.md` mapped to the OWASP LLM Top 10 (W14)

## Done when
Faithfulness ≥ 0.8, at least 90% of red-team cases are blocked, and every answer cites a source or escalates.
