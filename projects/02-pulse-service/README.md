# Project 2: Pulse in production (Weeks 6–8)

**Brief:** Ship the Pulse model as a service that survives traffic and failures.

## Deliverables
- [ ] FastAPI `/predict`, `/predict/batch`, `/health`: Pydantic schemas, API-key auth, rate limiting, OpenAPI docs (W6)
- [ ] A versioned model artifact (semver) loaded once at startup, with the joblib security trade-off documented (W6)
- [ ] pytest suite: schema, auth, prediction smoke tests (W6)
- [ ] Multi-stage non-root Dockerfile and docker-compose (W7)
- [ ] K8s manifests on kind: Deployment, Service, ConfigMap/Secret, probes, HPA, a rolling update with zero dropped requests (W7)
- [ ] AWS: ECR → ECS, plus an async path API → SQS → Lambda → DynamoDB (W8)
- [ ] Structured JSON logs, latency/error metrics, and `DESIGN.md` with an architecture diagram and failure modes (W8)

## Done when
A load test (e.g. `hey` or `locust`) at 50 rps shows p95 < 200 ms locally, and killing a pod drops no requests.
**Tear down your AWS resources once the work is reviewed.**
