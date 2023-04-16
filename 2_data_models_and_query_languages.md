1.Relational Model
=
SQL, data is organized into relations, where each relation (table)is an unordered collection pf tuples(rows).

NoSQL
=
A need for greater scalabilty than relational databases, including very large datasets or very high write throughput.

Specialized query operations that are not well supported by the relational model.

Frustration with restirictiveness of relational database, and desire for more dymamic and expressive data model.

The Object-Relational Mismatch
=
Most app development is done in OOP, if data is stored in relational tables, an awkward translation layer is required between code and database model table, rows, columns. This disconnect between the models is sometimes called an impedance mismatch.

The network model
=
The CODASYL model was a generalization of the hierarchical model. In the tree structure of the hierarchial model, a record has exactly one parent; In network model, a record could have multiple parents.

this allowed 1-1, 1-n relationship to be modeled.

The links between records in the network model were not foreign keys, but more like pointers in a programming language. The only way of accessing a record was to follow a path from a root record along these chain of link.

2.Document Models
=

The main argument in favor of the document data model are schema flexibility.(schema on read)

can not refer directly to a nested item within a document.

poor support for joins in document databases

a document is usually stored as a single continuous string.

The locality adventage is applies if you need large parts of the document at the same time.

it is generally recommented that you keep document small and avoid writes that increase the size of document.

Query Language for Data
=
Many conmmonly used programming language is imperative. whereas SQL is declarative query language.

An imperative language tells the computer  to perform certain operations in a certain order. A declarative language, you specify the pattern of the data you want.

declarative language is easy, and abstracted and also fast(parallel).

3.Graph-Like Data Models
=
You can think of a graph store as consisting of two relational tables, one for vertice and one for edges.

it is specialized for m-n relationships.

not enforce a schema.

