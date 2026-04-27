# Tool Contracts

Standardized tool contract templates for AI agent development.

## What is this?

A tool contract defines exactly how an AI agent interacts with an external tool. It eliminates guesswork and prevents 80% of production bugs caused by undefined tool behavior.

Built as part of the [ORBIRESEARCH](https://orbiresearch.com) four-layer agent architecture.

## Contract Structure

Every tool contract has 15 fields:

| Field | Purpose |
|-------|---------|
| Tool Name | Identifier |
| Category | Search, Extract, DB Write, Delivery, Memory, etc. |
| Purpose | What the tool does (one sentence) |
| Input Type | What it receives |
| Output Type | What it returns |
| Required Fields | Mandatory input fields |
| Optional Fields | Additional input fields |
| Validation Rule | How to verify input before calling |
| Failure Modes | How it typically breaks |
| Retry Allowed | Yes / No / Conditional |
| Fallback Exists | Yes / No / Conditional |
| Criticality | Low / Medium / High / Critical |
| Read or Write | Read / Write / Both |
| Security Notes | Safety constraints |
| Used By | Which agents use this tool |

## Example: Search Tool Contract

**Tool Name:** Tavily Search
**Category:** Search
**Purpose:** Searches relevant web sources by query
**Input Type:** Text query
**Output Type:** List of results with title, URL, and snippet
**Required Fields:** query
**Optional Fields:** language, region, result_limit
**Validation Rule:** Query must not be empty
**Failure Modes:** timeout, rate limit, API error, empty result
**Retry Allowed:** Conditional (timeout yes, invalid input no)
**Fallback Exists:** Yes (Exa as secondary search)
**Criticality:** High
**Read or Write:** Read
**Security Notes:** Results must not be accepted as validated without verification
**Used By:** Trend Hunter, Whale Tracker

## Why This Matters

Without tool contracts, your agent "figures out" how to use tools at runtime. Sometimes it guesses right. Sometimes it sends an empty query and treats the empty result as "no matches found."

One page per tool. That's all it takes to prevent this.

## License

MIT

## Links

- [ORBIRESEARCH](https://orbiresearch.com)
- [Full Methodology](https://orbiresearch.com/architecture)
