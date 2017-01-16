# Comparing result size estimations of two query optimizers

At my home university in Konstanz, we are currently working on a new query optimizer for the graph database Neo4j <sup>[1](#neo4j)</sup>. As a part of this work, I had to design good estimations of the result sizes of query execution plans. These estimations are needed in order to be able to estimate the physical cost of the execution of the corresponding plan.

Because the code is not yet public, I will just be able to explain the experimental setting and then analyse the results we obtained when we ran our tests. Our test stores these results as csv-files, which I will include in this repository.


<a name="neo4j">1</a>: [Neo4j](https://neo4j.com/) is a DBMS which in contrast to relational DBMS does not use tables but graph data structures. It also has a special graph oriented query language, called *Cypher*.
