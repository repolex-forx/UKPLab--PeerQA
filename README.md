# Repolex Knowledge Graph of UKPLab/PeerQA

RDF knowledge graph data for [UKPLab/PeerQA](https://github.com/UKPLab/PeerQA), parsed by [repolex](https://repolex.ai).

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
rlex download UKPLab/PeerQA
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d6d4170a9353cf61c2356e4100683601535a91e2
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── d6d4170a9353cf61c2356e4100683601535a91e2
│           └── chunk-001.nq.gz
├── blob
│   ├── 01a9bcb0da2d694c1229ad05083a899399861484.nq.gz
│   ├── 03d9d09a0c0d27534157e5126aabd2948bdb4aef.nq.gz
│   ├── 09cbf30e325830703eaf330cd350d07fcc09e8b7.nq.gz
│   ├── 1759739daa56448d7b269349045cdd9657cc3c9f.nq.gz
│   ├── 1dd545831698523323fc6dfa73a4b3b3db6db70a.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 40b873bc54ba901d57825e924b849ca029deccae.nq.gz
│   ├── 44ab5782020889b04edc788fc8b7f1f2dfba927c.nq.gz
│   ├── 4b4de5d61b2c3cae320ca653698c360a9bb5193c.nq.gz
│   ├── 65496077f8b988ceeeaad3c69afe45503706dd23.nq.gz
│   ├── 75e4f4fb21542ec16c2c71fe3cf444ebf7425ba9.nq.gz
│   ├── 75fde6644c619c5bcbd71f1dc8fee0eaf8f07545.nq.gz
│   ├── 7a61974a8585c4dd862ea8150ef308e1e0bc2173.nq.gz
│   ├── 81807b112a4809ee87820b90bf1ec50bb8e65cff.nq.gz
│   ├── 8210b16a3e9044d2dcdf8638abe56cf24a90c303.nq.gz
│   ├── 8ac3457efc3ea9e4130d5a41011cc436b8a3af87.nq.gz
│   ├── 8ad07c88b311e5f495aebc250f3b5d18c75e4e94.nq.gz
│   ├── 8fffbd100dde9fe492687a881c11b16df94a02d9.nq.gz
│   ├── a840e8f887a17bda0d9b5e14e80e65409d610b98.nq.gz
│   ├── a968191e3b73355de1e080bdc90d3fe3dcf6c85b.nq.gz
│   ├── b5741666c9c1e764f06c8ae6a7dd3c0321d01d17.nq.gz
│   ├── b978b942ed376f403fe42673f20d477feea65292.nq.gz
│   ├── c18495c73d38d0e631ae00d43231c14a4decdc43.nq.gz
│   ├── c8cfe3959183f8e9a50f83f54cd723f2dc9c252d.nq.gz
│   ├── d04bf08ad272fca68a5927f1cbf5f0f5a79f45ca.nq.gz
│   ├── d300647e03558604f8110277a4e9f9fdd9aa10a3.nq.gz
│   ├── daa2ea9a1bab9e3221eef3400fdc9f9a38101130.nq.gz
│   ├── daaeb7c1373258dabc2cdf94c841180a4e5b4584.nq.gz
│   ├── e2cb856e87a3e12007fed75e74cbd1f7ffe18845.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ebc90302d65ac0426a7e5b3a6764d0b463df0bbf.nq.gz
│   ├── ecb1b4f9f102a8626da225c05428135790985fdb.nq.gz
│   ├── ee87785cc964a7fca994d8228d27ef2e57e07150.nq.gz
│   └── faf97c4610cdb459ea408ca70a6c133f50c14f96.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── d6d4170a9353cf61c2356e4100683601535a91e2.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 42 files
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

[UKPLab/PeerQA](https://github.com/UKPLab/PeerQA)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
