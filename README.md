# Repolex Knowledge Graph of di/id

RDF knowledge graph data for [di/id](https://github.com/di/id), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download di/id
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4b37edb7db3b29aa2d147205a9466912ffd0c9b7
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 4b37edb7db3b29aa2d147205a9466912ffd0c9b7.nq.gz
│   └── repolex
│       └── 4b37edb7db3b29aa2d147205a9466912ffd0c9b7
│           └── chunk-001.nq.gz
├── blob
│   ├── 1359c679f5e607187fefe3cf20f68018989e8992.nq.gz
│   ├── 1ce7125c280dd2d951d3b0abf372efefd4a9a60c.nq.gz
│   ├── 24480e5c0535ee35511c50730d8c02eea741783b.nq.gz
│   ├── 347431bda12b369d9f9bc69d1a9c11b5d210c6f4.nq.gz
│   ├── 35d3db473df5ff58108ed383a9f3d14976911a82.nq.gz
│   ├── 3890e8a4e5f67b5ece7278ba70bc44ca3565ba18.nq.gz
│   ├── 39024244704905ca9820b94a80d8734966c7b5ce.nq.gz
│   ├── 4dc3b2fb964cc0e4e69c13af786fab95825e2052.nq.gz
│   ├── 5f2c003d6d169bf7351c8368da9172aa978e5e21.nq.gz
│   ├── 697517e4ad5dca8b9ec6c2f495e31171ea1dde5e.nq.gz
│   ├── 7002a7d63771601adf20eb582bb21685ad55742a.nq.gz
│   ├── 77b475eea955e41fc6d87adf20dc7c04baf071d0.nq.gz
│   ├── 825a94c5cfbf62e4f92f5a53fb15ee959e4e1c82.nq.gz
│   ├── 87268312a9c9c5b60d341f9f2450af9770b01145.nq.gz
│   ├── 88cb71fa9e400e62c1b904a0d332ffea2d7ee1c6.nq.gz
│   ├── 9154db471182f59f48977c3074fcacdf33f050c0.nq.gz
│   ├── 9899c4b51cc768a0cee0ac7a86fba702d217b44e.nq.gz
│   ├── a5d59a41a8f698b1ac67472cb2e633fbccab3e74.nq.gz
│   ├── cc2fb75de3adc328b70d3f256e068cf91543ed2a.nq.gz
│   ├── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
│   ├── dbed0b0db3f0b0dc1880285d07c960272eb58dcc.nq.gz
│   └── f3884abfd3e1b88dfa01cef323c4e40b02c8b0fc.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 4b37edb7db3b29aa2d147205a9466912ffd0c9b7.nq.gz
├── filetree
│   └── 4b37edb7db3b29aa2d147205a9466912ffd0c9b7.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 32 files
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

## Source repository

[di/id](https://github.com/di/id)

---
*Parsed on 2026-04-14 by [repolex](https://repolex.ai)*
