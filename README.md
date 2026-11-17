
# Nexus

Nexus is a multi-tenant email campaign platform built using a
microservices architecture.

The project focuses on building a scalable, reliable and observable
backend system with independent services and asynchronous processing.

## Architecture

Nexus follows a monorepo structure with independently deployable
microservices.

### Planned services

- API Gateway
- Identity Service
- Tenant Service
- Campaign Service
- Scheduler Service
- Dispatch Service
- Provider Service
- Webhook Service
- Alerting Service

### Technology Stack

- Runtime: Node.js 24
- Language: TypeScript
- Framework: Express.js 5
- Package Manager: npm workspaces
- Database: PostgreSQL
- Cache: Redis
- Messaging: Apache Kafka
- Internal Communication: gRPC / Protocol Buffers
- External APIs: REST
- Containerization: Docker
- Orchestration: Kubernetes

## Repository Structure

```text
nexus-platform/
├── apps/
│   └── api-gateway/
├── packages/
├── infrastructure/
│   ├── docker/
│   └── kubernetes/
├── docs/
│   ├── architecture/
│   └── adr/
├── .github/
│   └── workflows/
├── package.json
├── package-lock.json
├── tsconfig.base.json
├── .nvmrc
└── README.md
```

## Prerequisites

- Node.js 24
- npm

## Getting Started

Clone the repository:

```bash
git clone <repository-url>
cd nexus-platform
```

Use the configured Node.js version:

```bash
nvm install
nvm use
```

Install dependencies:

```bash
npm install
```

## Development

Services are maintained as independent npm workspaces.

Example:

```bash
npm install express --workspace=@nexus/api-gateway
```

## Project Status

Currently under active development.

The initial milestone focuses on repository setup, service
bootstrapping, configuration management, health checks and CI.

## License

TBD
```

Replace `<repository-url>` once your GitHub repository is ready.

## 4. Generate `package-lock.json`

From the repository root:

```bash
npm install
```

This generates or updates the root `package-lock.json` based on your root package configuration and workspaces.

**Do not generate separate lockfiles inside individual services.** Nexus will use one root lockfile.

## 5. Verify repository hygiene

Run:

```bash
git status --short
```

Check that the lockfile exists:

```bash
ls -la package-lock.json .gitignore .nvmrc README.md
```

Verify the Node version:

```bash
cat .nvmrc
node --version
```

---

## NEXUS-001 — Updated checklist

{@body const tasks = ["Root .gitignore created","Node.js 24 configured in .nvmrc","README.md created","Root package-lock.json generated","npm install succeeds","Git status reviewed"]}
{@body const [done,setDone] = DIL.useState([])}
<box border radius="lg" padding={3} gap={3}>
  <row align="center" justify="between">
    **Repository hygiene**
    <title size="lg" color="default" tabularNums>{done.length}/{tasks.length}</title>
  </row>
  <box background="surface-tertiary" height="6px" radius="full" clip>
    <box background="surface-inverted" height="6px" radius="full" width={`${done.length/tasks.length*100}%`} />
  </box>
  {#each tasks as task,i}
    <checkbox key={i} checked={done.includes(i)} onChange={v=>setDone(old=>v?[...old,i]:old.filter(x=>x!==i))}>{task}</checkbox>
  {/each}
</box>

**Time budget:** 20–25 minutes.

Once completed, share your `.gitignore`, `.nvmrc`, README and root `package.json`, along with the output of `npm install`.

I'll review the work and verify NEXUS-001's definition of done before assigning NEXUS-002.