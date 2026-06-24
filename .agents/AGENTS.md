# AI Platform Engineering Agent Workspace

This `.agents` directory serves as the "brain" for the project. All AI code generation and structural changes must follow the workflows and rules defined here.

## Structure
- `context/`: Contains the ground truth for our architecture, database schema, and UI registry. Agents must consult these before modifying code.
- `workflows/`: Defines the strict loops (Architect -> Review -> Imprint) for specific tasks.
- `skills/`: Contains custom scripts and tools for validation and code enforcement.
- `feature-specs/`: Stores the numbered, approved implementation plans (`01-feature.md`) for permanent documentation of what the AI has built.
