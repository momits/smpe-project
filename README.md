# Comparing result size estimations of two query optimizers

At my home university in Konstanz, we are currently working on a new query optimizer for the graph database Neo4j [1](#neo4j). Our optimizer is based on the Cascades framework [2](#cascades), which comes from the relational database world. As a part of this work, I had to design good estimations of the result sizes of queries. These estimations are needed in order to be able to estimate the time needed to physically execute the query with a corresponding execution plan.

The questions I would like to analyse here, are the following:
- On which kinds of queries does the Cascades optimizer have better estimations?
- On which kinds of queries does the Neo4j optimizer have better estimations?
- Which optimizer produces overall better estimations for a given set of queries in a given database?

Because the code is not yet public, I will just be able to explain the experimental setting and then analyse the results we obtained when we ran our tests, without giving a recipe for reproduction. Our test stores these results as csv-files, which I will include in this repository.

The analysis will be performed in a RMarkdown document.

<a name="neo4j">1</a>: [Neo4j](https://neo4j.com/) is a DBMS which in contrast to relational DBMS does not use tables but graph data structures. It also has a special graph oriented query language, called *Cypher*.

<a name="cascades">2</a>: [Cascades](https://pdfs.semanticscholar.org/360e/cdfc79850873162ee4185bed8f334da30031.pdf) is a framework for query optimization.
