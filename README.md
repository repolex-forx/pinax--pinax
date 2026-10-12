# Repolex Knowledge Graph of pinax/pinax

RDF knowledge graph data for [pinax/pinax](https://github.com/pinax/pinax), parsed by [repolex](https://repolex.ai).

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
rlex download pinax/pinax
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5a3b55788f802da5bf5728b1ca67b90593c91206
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5a3b55788f802da5bf5728b1ca67b90593c91206
│           └── chunk-001.nq.gz
├── blob
│   ├── 092f79a86860da341a92762a398f7f3f16f7c925.nq.gz
│   ├── 139b0d6924e2d1e3fa4e4b12c6e7ff3f964a8c2c.nq.gz
│   ├── 27f560044e1efed8e76cf52779996e87f9660acd.nq.gz
│   ├── 3014f97c11bb8a0b739ea4ef6e52b33ff851595a.nq.gz
│   ├── 3d55505d18f4a040050d1d676133b50f19536bf9.nq.gz
│   ├── 4084fbb0beadd785d0bcb59e4057999dd712f241.nq.gz
│   ├── 4253e8b2fb99b7eac455eb7722a70384d4709c36.nq.gz
│   ├── 4d436ca6d489c13ec0785ac430956a829fb4d204.nq.gz
│   ├── 4fcacc70bc3e83d28ea764f9318cd8be467dff17.nq.gz
│   ├── 525943f51bb8d7b3865cbda7f5483882896b3305.nq.gz
│   ├── 5bd445f8745ed8d79215173d119c8a980c499b32.nq.gz
│   ├── 63b058ee71315cea23ba59f5170135cc3f993f32.nq.gz
│   ├── 85a84ea8b39fe2484d29b6ac9988a2803882ab62.nq.gz
│   ├── a2d0e2c9d3c3e31b67af84c770fd8b2ac626eb45.nq.gz
│   ├── aa63f26d068147a30684dd32d5897553893fa63b.nq.gz
│   ├── af7d5d4f5a01e21a3d67fa74d8d533c3aa25cbaf.nq.gz
│   ├── cad9fe2ba291f2cebc2f321810d86206bd4088c2.nq.gz
│   ├── dc05474b53c46b131802e9d15465022503339b3e.nq.gz
│   ├── e6230d5f997aa3b953f8feb670c7b13b66d377e6.nq.gz
│   ├── ef6e4df31b9c24267946a803601da8fa87b3b16b.nq.gz
│   ├── f78599f3897963e4e6e75c9e1a44d2b88cc0edc2.nq.gz
│   ├── f9721c806d38b0e039de64356dbe7ac507073377.nq.gz
│   ├── fbd51e9abc466bb6a9f1e563d3baa06eae2acbff.nq.gz
│   └── fc8f702b5da04963b7be59f09090c5a002cde263.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5a3b55788f802da5bf5728b1ca67b90593c91206.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 32 files
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

[pinax/pinax](https://github.com/pinax/pinax)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
