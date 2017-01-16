# Comparing result size estimations of two query optimizers

At my home university in Konstanz, we are currently working on a new query optimizer for the graph database Neo4j <sup>[1](#neo4j)</sup>. Our optimizer is based on the Cascades framework <sup>[2](#cascades)</sup>, which comes from the relational database world. As a part of this work, I had to design good estimations of the result sizes of queries. These estimations are needed in order to be able to estimate the time needed to physically execute the query with a corresponding execution plan.

The questions I would like to analyse, are the following:
- On which kinds of queries does the Cascades/Neo4j optimizer have better estimations?
- How are actual query size and estimated size correlated for different kinds of queries?
- Which optimizer produces overall better estimations for a given set of queries in a given database?

Because the code is not yet public, I will just be able to explain the experimental setting and then analyse the results we obtained when we ran our tests, without giving a recipe for reproduction. This is not a huge problem however, because the size estimations are purely logical and can be measured on any system. The estimated result sizes will be available as csv-files in this repository.

The analysis will be performed in [this]() RMarkdown document.

## Setting

As explained, a query optimizer has to be able to estimate the result size of
an arbitrary query:

```
 -------------
|             |
|  Database   |-------\
|             |       |        ----------
 -------------        \------>|           |
                              | Optimizer |-------> Estimated result size
 -------------        /------>|           |
|             |       |        -----------
|    Query    |-------/
|             |
 -------------
```

Our test takes a database and a set of queries on this database as input.
It outputs a CSV-file containing the actual result size of the query and the
estimated sizes of the optimizers:

```
 -------------
|             |
|  Database   |-------\
|             |       |        ----------
 -------------        \------>|           |
                              |    Test   |--> CSV(QueryId|ResultSize|Optimizer|EstSize)
 -------------        /------>|           |
|   Catalog   |       |        -----------
|     of      |-------/
|   queries   |
 -------------
```

## Databases

For this analysis we consider the following two databases:

- The *MovieDb* <sup>[3](#moviedb)</sup>. A database on movies, actors, directors, their relations etc.

- The *SocialNetworkDb* <sup>[4](#socialnetworkdb)</sup>. A database designed to imitate a social network.

For the sets of queries tested on these databases, please refer to the [analysis document]().



<a name="neo4j">1</a>: [Neo4j](https://neo4j.com/) is a DBMS which in contrast to relational DBMS does not use tables but graph data structures. It also has a special graph oriented query language, called *Cypher*.

<a name="cascades">2</a>: <https://pdfs.semanticscholar.org/360e/cdfc79850873162ee4185bed8f334da30031.pdf>

<a name="moviedb">3</a>: <https://www.themoviedb.org/>

<a name="socialnetworkdb">4</a>: <http://ldbcouncil.org/developer/snb>


