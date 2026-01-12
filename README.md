# MCP Weather and Air Quality Explorer

This repository contains a Google Colab notebook that demonstrates how to use the **Model Context Protocol (MCP)** to interact with external tools in a standardized, protocol-driven way.

The notebook connects to a publicly available MCP weather server (**no API keys required**), dynamically discovers its tools, and retrieves:

- Current weather for multiple cities
- Air quality summaries
- Detailed pollutant metrics (PM2.5, PM10, ozone, NO₂, etc.)

All interactions follow the **MCP specification** rather than hardcoded API logic.

---

## What is MCP?

**MCP (Model Context Protocol)** is an open protocol that defines how AI systems and clients communicate with external tools, services, and data sources.

Instead of integrating each API manually, MCP provides:

- A standard way to discover tools  
- A uniform way to call tools  
- A structured way to receive results  
- A consistent lifecycle handshake  
- A clear client–server separation  

MCP is built on **JSON-RPC** and defines a semantic layer on top of it that enables AI agents and applications to interact with tools dynamically.

In MCP:

- A **server** exposes tools (weather, databases, search, file systems, etc.)
- A **client** discovers and calls those tools
- Both sides communicate using a **standard protocol**

---

## MCP vs REST APIs

MCP and REST solve similar problems but in very different ways.

### REST API Model

In a REST-based system:

- Endpoints are hardcoded
- Schemas are manually integrated
- Documentation is external
- Versioning is brittle
- Clients must be rewritten when APIs change


Each API requires custom integration logic.

---

### MCP Model

In MCP:

- Tools are discovered dynamically
- Input/output schemas are machine-readable
- Tool metadata is included
- Clients are protocol-driven
- Servers can be swapped without changing client logic

**Typical MCP flow:**

Client → tools/list → tools/call → standardized response
---

### Key Differences

| Feature | REST | MCP |
|--------|------|-----|
| Hardcoded endpoints | Yes | No |
| Dynamic tool discovery | No | Yes |
| Self-describing schema | No | Yes |
| Protocol lifecycle | No | Yes |
| AI-native | No | Yes |
| Vendor lock-in | High | Low |
| Tool chaining | Manual | Built-in |
| Agent compatibility | Low | High |

---

## Purpose of This Repository

This repository demonstrates how MCP works in practice by building a complete client workflow:

- Starting a local MCP server
- Performing the MCP handshake
- Discovering tools dynamically
- Calling weather and air quality tools
- Parsing natural-language outputs
- Converting them into structured tables
- Running batch queries for multiple cities

The notebook is designed to be:

- Fully open-source
- No API keys required
- Colab-compatible
- Beginner-friendly
- Protocol-first
- Vendor-agnostic

---

## What the Notebook Covers

### 1. Server Setup

The notebook launches a local MCP server over standard input/output (stdio).

---

### 2. MCP Handshake

The client performs the required MCP lifecycle:

- `initialize`
- `initialized`

This step is mandatory before any tool calls.

---

### 3. Tool Discovery

The client retrieves the list of tools using:

- `tools/list`

This avoids hardcoding any tool names or schemas.

---

### 4. Weather Queries

The notebook calls:

- `get_current_weather`

It extracts:

- Temperature
- Weather condition

The results are normalized into a table.

---

### 5. Air Quality Queries

The notebook calls:

- `get_air_quality`
- `get_air_quality_details`

It extracts:

- AQI summary
- Pollutant values (PM2.5, PM10, NO₂, O₃, etc.)

These are parsed and converted into structured columns.

---

## Why MCP Matters

MCP enables:

- Tool-agnostic clients
- Interoperable ecosystems
- Modular architectures
- AI-native workflows
- Future-proof integrations

This notebook shows how MCP can replace brittle, custom API glue with a single standardized interface.

---

## Curated Lists of MCP Servers

If you want to explore more MCP servers, these curated lists are excellent starting points:

### Awesome MCP Servers
A community-maintained list of publicly available MCP servers.  
🔗 https://github.com/punkpeye/awesome-mcp-servers

---

### MCP Servers Directory
A browsable directory of MCP servers.  
🔗 https://mcpservers.org

---

### MCP Marketplace
Registry of MCP servers and integrations.  
🔗 https://github.com/cline/mcp-marketplace


**Typical REST flow:**

