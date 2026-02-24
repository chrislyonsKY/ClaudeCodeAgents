# Agentic Automation Template — Python (Package-First)

## Overview
Production-ready Python architecture structured as an installable package.

## Directory Structure
project-folder/
├── pyproject.toml
├── src/
│   └── project_name/
│       ├── cli.py
│       ├── orchestrator.py
│       ├── config/
│       ├── core/
│       ├── processors/
│       ├── integrations/
│       ├── io/
│       └── reports/
├── tests/
├── logs/
├── run_history.json
└── ai-dev/

## Design Principles
- No module-level globals
- Structured + legacy logging
- Dynamic transfer window
