# Repolex Knowledge Graph of google/gofuzz

RDF knowledge graph data for [google/gofuzz](https://github.com/google/gofuzz), parsed by [repolex](https://repolex.ai).

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
rlex download google/gofuzz
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5dfa3b7056d4abdb26b76c43d012ebe151e8a33c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5dfa3b7056d4abdb26b76c43d012ebe151e8a33c
│           └── chunk-001.nq.gz
├── blob
│   ├── 18c3fc4997076082d98131ea8c70f60ffb3bef58.nq.gz
│   ├── 5bb365949691eb734286d4b8b3e2ff78acaf5d86.nq.gz
│   ├── 5d280e9737394e319ec06b1ba3cccb8dd3b2f448.nq.gz
│   ├── 6e99d9d987b54a331c724ed8cfd9cdef7fb27b82.nq.gz
│   ├── 8ec4fe9e9725a847099325d5b886eaae40b2e660.nq.gz
│   ├── 97c1b34fd5e6c7c6b45d61aba8a2d64d8430dd89.nq.gz
│   ├── 9f9956d4a64febc2ee9a242e02728f4abd2dfa2b.nq.gz
│   ├── a7297907a1eb4eb69884095375207314046afa19.nq.gz
│   ├── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
│   └── e1a8f54f3744d9e0e5495de17b4096e94c38ee97.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5dfa3b7056d4abdb26b76c43d012ebe151e8a33c.nq.gz
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

[google/gofuzz](https://github.com/google/gofuzz)

---
*Parsed on 2026-11-10 by [repolex](https://repolex.ai)*
