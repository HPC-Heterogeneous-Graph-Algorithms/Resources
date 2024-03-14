---
layout: default
title: Graph datasets
nav_order: 1
permalink: /graph-datasets/source
has_children: false
---

We can generally find real world graphs in the links below:

| Name                      | Link                                                                                          | Graph format  |
|---------------------------|-----------------------------------------------------------------------------------------------|---------------|
| All datasets combined     | [https://networkrepository.com](https://networkrepository.com)                                |               |
| spare suit matrix         | [http://sparse.tamu.edu/](http://sparse.tamu.edu/)                                            | .mtx          |
| SNAP                      | [https://snap.stanford.edu/data/](https://snap.stanford.edu/data/)                        | Edge list(.txt)|
| LAW                       | [https://law.di.unimi.it/datasets.php]( https://law.di.unimi.it/datasets.php)                     | webgraph  |
| BioGraphs                 | [https://blogs.qub.ac.uk/dipsa/ms-biographs-ms/](https://blogs.qub.ac.uk/dipsa/ms-biographs-ms/)  | webgraph  |
| Lemur (clueweb09/12/22)   | [https://www.lemurproject.org/clueweb09.php/](https://www.lemurproject.org/clueweb09.php/)        |           |
| Konect                    | [http://konect.cc/networks/](http://konect.cc/networks/)                                          |           |
| Hyper Link Graphs         | [http://webdatacommons.org/hyperlinkgraph/](http://webdatacommons.org/hyperlinkgraph/)            | webgraph and edgelist |


## Resources:

- [https://lgylym.github.io/big-graph/dataset.html](https://lgylym.github.io/big-graph/dataset.html)
- [http://gap.cs.berkeley.edu/datasets.html](http://gap.cs.berkeley.edu/datasets.html)
- [https://projects.csail.mit.edu/dnd/](https://projects.csail.mit.edu/dnd/)
- [https://graphchallenge.mit.edu/data-sets](https://graphchallenge.mit.edu/data-sets)

## Protein to Protein interactions to graph 

- [protein database string](https://string-db.org/cgi/access?sessionId=baYXb3oJoc4T&footer_active_subpage=archive)
- [SNAP Miner](https://github.com/snap-stanford/miner-data/tree/master) to extract the data.

## Extracting webgraph

- [webgraph](https://webgraph.di.unimi.it/)
- [webgraph source](https://github.com/vigna/webgraph)
- [Webgraph Documentation](https://webgraph.di.unimi.it/docs/)
- [webgraph Large source](https://github.com/vigna/webgraph-big) for graphs with vertices greater than $2^{31}$
- [webgraph Large Documentation](https://webgraph.di.unimi.it/docs-big/)

### Installing

- Need Java greater than 9.
- Add `Ant` and `Ivy` 
- Run : `ant ivy-setupjars jar`
- set your `CLASSPATH` by `source setcp.sh`
- Download the `{source}.graph` and possibly `{source}.properties`.
- Then run: `java -server it.unimi.dsi.webgraph.ASCIIGraph sourcebasename dest`


