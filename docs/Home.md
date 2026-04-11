---
layout: default
title: Home
nav_order: 1
permalink: /
has_children: false
---

# HPC Resources
{: .fs-9 .fw-700 }

Graph formats, converters, datasets and tools for high-performance parallel and distributed graph algorithms.
{: .fs-5 .fw-300 }

[Graph Formats →](https://hpc-heterogeneous-graph-algorithms.github.io/Graph-Formats/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Format Converters →](https://github.com/HPC-Heterogeneous-Graph-Algorithms/graph-format-converters){: .btn .btn-outline .fs-5 .mb-4 .mb-md-0 }

---

## Graph Formats

Standard representations used across our tools and benchmarks. Full specifications at the [Graph Formats documentation site](https://hpc-heterogeneous-graph-algorithms.github.io/Graph-Formats/).

| Format | Type | Node IDs | Description |
|:-------|:-----|:---------|:------------|
| **[BGR](https://hpc-heterogeneous-graph-algorithms.github.io/Graph-Formats/bgr)** | Binary (CSR) | 0-indexed | Binary Graph Representation — compact CSR with adaptive uint32/uint64, parallel I/O, weighted/unweighted support |
| **[MTX](https://hpc-heterogeneous-graph-algorithms.github.io/Graph-Formats/mtx)** | Text (Matrix Market) | 1-indexed | Widely used text format for sparse matrices — human-readable edge list with header metadata |
| **[BVGraph](https://hpc-heterogeneous-graph-algorithms.github.io/Graph-Formats/bvgraph)** | Compressed binary | 0-indexed | WebGraph's compressed format — gamma/delta/zeta coded successor lists, used by LAW datasets |
| **[ECL](https://hpc-heterogeneous-graph-algorithms.github.io/Graph-Formats/ecl)** | Binary (CSR) | 0-indexed | ECL graph format — simple binary CSR used by ECL-MIS, ECL-CC, ECL-BCC and related GPU algorithms |
| **[WGBin](https://hpc-heterogeneous-graph-algorithms.github.io/Graph-Formats/wgbin)** | Binary | 0-indexed | WebGraph binary — intermediate raw format for BVGraph decoding pipelines |

---

## Graph Format Converters

The [graph-format-converters](https://github.com/HPC-Heterogeneous-Graph-Algorithms/graph-format-converters) repo converts WebGraph BVGraph compressed graphs (`.graph` + `.properties`) from the [LAW dataset collection](http://law.di.unimi.it/datasets.php) into standard formats.

### Tools

| Tool | Description |
|:-----|:------------|
| `bvgraph_gen_offsets` | Generate `.offsets` from `.graph` + `.properties` (pure C++, no Java) |
| `bvgraph_to_bgr` | Convert BVGraph → BGR (binary CSR) |
| `bvgraph_to_mtx` | Convert BVGraph → MTX (Matrix Market text) |

### Quick Start

```bash
# Build C++ tools (no Java required)
make cpp

# Download a graph (example: eu-2005, 862K nodes, 19M edges)
mkdir -p data
wget -P data http://data.law.di.unimi.it/webdata/eu-2005/eu-2005.graph
wget -P data http://data.law.di.unimi.it/webdata/eu-2005/eu-2005.properties

# Generate offsets, then convert to BGR
./bvgraph_gen_offsets data/eu-2005
./bvgraph_to_bgr data/eu-2005 data/eu-2005.bgr 8
```

### Performance

Multi-threaded C++ (4 threads) converts BGR at **~150M edges/s**.

| Pipeline | MTX time | BGR time |
|:---------|:---------|:---------|
| C++ | 0.68s | 0.26s |
| Java | 1.76s | 0.52s |
| **Speedup** | **2.6×** | **2.0×** |

Benchmarked on eu-2005 (862K nodes, 19M edges), single thread.

---

## Graph Datasets

Browse our curated collection of real-world and synthetic graphs:

- [**Large Graphs**]({{ site.baseurl }}/graph-datasets/large-graphs) — Graphs with 500M+ edges (web crawls, social networks, genomics, up to 2.5 trillion edges)
- [**Sources**]({{ site.baseurl }}/graph-datasets/source) — Where to find graph datasets (SNAP, LAW, SuiteSparse, KONECT, BioGraphs, and more)

---

## Related Repositories

| Repository | Description |
|:-----------|:------------|
| [Graph-Formats](https://github.com/HPC-Heterogeneous-Graph-Algorithms/Graph-Formats) | Documentation site for graph format specifications (BGR, MTX, BVGraph, ECL, WGBin) |
| [graph-format-converters](https://github.com/HPC-Heterogeneous-Graph-Algorithms/graph-format-converters) | C++ and Java tools to convert WebGraph BVGraph → BGR / MTX |
| [SCC Analysis](https://github.com/LokeshVenkatachalam/Strongly-Connected-Components-Analysis) | Benchmark of 4 parallel SCC algorithms on graphs up to 92 billion edges |
| [BCC-Finding](https://github.com/HPC-Heterogeneous-Graph-Algorithms/BCC-Finding) | Biconnected components algorithms |
| [PHEM](https://github.com/HPC-Heterogeneous-Graph-Algorithms/PHEM) | Parallel heterogeneous graph algorithms |
