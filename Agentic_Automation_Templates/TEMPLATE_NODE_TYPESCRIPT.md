# Agentic Automation Template — Node.js + TypeScript

## Overview
Scalable architecture for ETL, automation, and semi-agentic systems using Node.js + TypeScript.

## Directory Structure
project-folder/
├── package.json
├── tsconfig.json
├── src/
│   ├── cli/
│   ├── orchestrator/
│   ├── config/
│   ├── core/
│   ├── processors/
│   ├── integrations/
│   ├── io/
│   └── reports/
├── tests/
├── logs/
├── run_history.json
└── ai-dev/

## Design Principles
- No global mutable state
- RunContext manages runtime
- Continue-on-error orchestration
- Structured logging
