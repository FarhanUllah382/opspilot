# Contracts

Shared agreements between the three parts of OpsPilot. **Any change here needs approval from all three members**,
because the other parts depend on these exact names and shapes.

| File | Defines |
| --- | --- |
| `incident_state.json` | The LangGraph shared state, one example incident |
| `mcp_tools.md` | Every MCP tool: name, inputs, output |
| `api_endpoints.md` | Every Express API endpoint |
| `scenarios.md` | The four failure scenarios and their correct answers |

Incident statuses, in order: `detected` → `investigating` → `awaiting_approval` → `executing` →
`resolved` | `fix_ineffective` | `rejected` | `no_incident` | `failed`.
