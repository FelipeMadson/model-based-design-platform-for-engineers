# Model-Based Design Platform for Engineers

[![CI Status](https://github.com/FelipeMadson/model-based-design-platform-for-engineers/actions/workflows/ci.yml/badge.svg)](https://github.com/FelipeMadson/model-based-design-platform-for-engineers/actions)
[![Latest Release](https://img.shields.io/github/v/release/FelipeMadson/model-based-design-platform-for-engineers?color=145e4d&logo=github)](https://github.com/FelipeMadson/model-based-design-platform-for-engineers/releases)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)
[![SemVer 2.0.0](https://img.shields.io/badge/semver-2.0.0-blue.svg)](https://semver.org)

[![CI Status](https://github.com/FelipeMadson/model-based-design-platform-for-engineers/actions/workflows/ci.yml/badge.svg)](https://github.com/FelipeMadson/model-based-design-platform-for-engineers/actions)
[![Latest Release](https://img.shields.io/github/v/release/FelipeMadson/model-based-design-platform-for-engineers?color=145e4d&logo=github)](https://github.com/FelipeMadson/model-based-design-platform-for-engineers/releases)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)
[![SemVer 2.0.0](https://img.shields.io/badge/semver-2.0.0-blue.svg)](https://semver.org)

[![Node.js Version](https://img.shields.io/badge/Node.js-22%20%7C%2024%20LTS-brightgreen.svg)](https://nodejs.org)
[![Architecture](https://img.shields.io/badge/Architecture-Clean%20Hexagonal%20Multi--Tenant-blue.svg)](docs)
[![Test Suite](https://img.shields.io/badge/Tests-100%25%20Passing%20(18%20tests%20node%3Atest)-success.svg)](tests)
[![Security](https://img.shields.io/badge/Security-TimingSafeEqual%20%7C%20Zero--Leak-success.svg)](src/security)
[![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)](LICENSE)

> **Engineers and scientists use outdated, monolithic tools for complex system design and simulation tasks.**

---


---

## 🖥️ Demonstração em Terminal Vetorial (Execução & Benchmarks)

<p align="center">
  <img src="docs/assets/terminal-demo.svg" alt="Terminal Demo - Model Based Design Platform For Engineers" width="840" />
</p>

## 🏛️ Visão Geral & Arquitetura de Software

O **Model-Based Design Platform for Engineers** foi construído seguindo princípios de **Engenharia de Software de Alto Rigor Corporativo**, estruturado em camadas desacopladas (Clean / Hexagonal DDD) e operando com **100% de APIs nativas do Node.js** (zero dependências externas de runtime).

```mermaid
flowchart TD
    CLI["CLI / Consumer Input"] --> Domain["Domain Layer (Value Objects & Invariants)"]
    Domain --> Engine["Core Multi-Tenant Engine"]
    
    subgraph Layers["Subsistemas de Alta Resiliência"]
        Engine --> Security["Security Vault (Timing-Safe HMAC / Zero-Leak)"]
        Engine --> WAL["Storage WAL (Write-Ahead Log + Crash Recovery)"]
        Engine --> Outbox["Outbox Dispatcher (Idempotência)"]
        Engine --> RateLimiter["Token-Bucket Rate Limiter"]
        Engine --> CircuitBreaker["Circuit Breaker (CLOSED / OPEN / HALF_OPEN)"]
        Engine --> EventBus["Event Bus (Domain Events Pub/Sub)"]
        Engine --> Telemetry["Prometheus Exporter (P50/P95/P99)"]
    end
    
    Security --> Output["Audit Verified Record"]
```

---

## 🚀 Diferenciais Técnicos de Nível Staff/Senior

* **Zero Runtime Dependencies:** Total independência de ecossistemas externos, garantindo menor superfície de ataque e inicialização instantânea (< 30ms).
* **Multi-Tenancy Criptograficamente Segregado:** Cada registro é isolado por TenantIdentifier e protegido contra vazamento entre contas.
* **Proteção Criptográfica Contra Side-Channel:** Comparação de hashes via `crypto.timingSafeEqual` prevenindo ataques de canal lateral baseados em tempo de resposta.
* **Higienização Recursiva Automática (Zero Credential Leak):** Algoritmo profundo que mascara chaves de API, senhas e tokens antes de persistir no log.
* **Write-Ahead Logging (WAL) com Recuperação de Desastres:** Reconstrução determinística de estado através de `replay()` validado por somas de verificação SHA-256.
* **Resiliência Integrada:** Algoritmo Token-Bucket para controle de taxa e Circuit Breaker para tolerância a falhas.
* **Telemetria Prometheus Nativa:** Cálculo de percentis de latência (P50, P95, P99) e métricas expostas no formato oficial.

---

## 🛠️ Instalação & Execução

```bash
# Executa a suíte corporativa de 18 testes automatizados
npm test

# Executa o benchmark de performance integrado (> 5.000 ops/seg)
npm run cli benchmark

# Inspeciona as estatísticas e saúde do motor
npm run cli status

# Diagnóstico de integridade do ambiente
npm run cli doctor
```

---

## 👤 Autor & Licença

* **Autor:** Felipe Madison ([@FelipeMadson](https://github.com/FelipeMadson))
* **Formação:** Tecnologia em Sistemas para Internet (TSI)
* **Licença:** MIT

---

## 📦 Polyglot Client SDKs (TypeScript & Python)

SDKs tipados com zero dependências externas em `sdk/`:

```typescript
import { modelbaseddesignplatformforengineersClient } from "./sdk/ts/client.ts";
const client = new modelbaseddesignplatformforengineersClient({ baseUrl: "http://127.0.0.1:3000" });
const health = await client.checkHealth();
console.log("Health:", health.status);
```
