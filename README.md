# Repolex Knowledge Graph of simonw/llm-typesafe

RDF knowledge graph data for [simonw/llm-typesafe](https://github.com/simonw/llm-typesafe), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download simonw/llm-typesafe
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 225932cfde461ee6e38ae2b612040c50c086db8c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 225932cfde461ee6e38ae2b612040c50c086db8c
│           └── chunk-001.nq.gz
├── blob
│   ├── 25e01603a2346de7f84cee33e3810eccf5cdc524.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 38ba85e698cbdabd0c7e5aa5abe7b2fb6a4fd5a0.nq.gz
│   ├── 509b705179c90d07a9e8ae813cafaf7259b5f399.nq.gz
│   ├── 62d78ba3bcb8239f30f6e6ac35a6344826524312.nq.gz
│   ├── 8433b121acb46137ab14ed4ad03d09dc3bbcbe5d.nq.gz
│   ├── 8c853af6d83c999b7e95de091fa67ab965ee0493.nq.gz
│   ├── a04993d4f91c69f728cef83bfc34b11054936e89.nq.gz
│   ├── d0d5ce3ee8fa6494d61b4f902ee7d8de943e1b36.nq.gz
│   └── dd6387adbca3ab87ab855d7bd355071cb445fff5.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 225932cfde461ee6e38ae2b612040c50c086db8c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[simonw/llm-typesafe](https://github.com/simonw/llm-typesafe)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
