# Agentic Automation Template — ArcGIS Pro SDK Add-In

## Overview
Workflow automation template for ArcGIS Pro SDK (C# + MVVM).

## Directory Structure
project-folder/
├── ProjectName.sln
├── src/
│   └── ProjectName.AddIn/
│       ├── Config.daml
│       ├── Module1.cs
│       ├── Views/
│       ├── ViewModels/
│       ├── Orchestration/
│       ├── Core/
│       ├── Services/
│       └── Reports/
├── logs/
├── run_history.json
└── ai-dev/

## Design Principles
- MVVM compliance
- QueuedTask-safe edits
- Continue-on-error orchestration
