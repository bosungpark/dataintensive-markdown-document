Log-structured storage engine
=
high throughput in write

Hash Indexes
=
It is well suit to situation where the value for each key is updated frequently.

Using it, Bitcask log data with apped-only log. if there is duplicated value, merge data. it seem wastful.

But appending and segment merging are sequential write operation, which are generally much faster than random writes. and concurreny and crash recovery are much simpler if segment files are append-only or immutable. and also merging old segment avoid data files got fragmented over time.

However also have limitation. The hash table must fit the memory and range queries are not efficient.

SSTable and LSM-Trees
=
The sepuence of Key-value pairs is sorted by key; Sorted String Table. we also require that each key only appears once within each merged segement file. SSTable have big adventage over log segments with hash indexes.

Merging segments is simple and efficient, even if files are bigger than the available memory.(merge sort algorithm)

And in order to find a particular key in the file, you no longer need to keep and index of all the keys in memory.

if the databse crashes, the most recent writes are lost. In order to avoid that problem, we can separate log on disk to which every write is immediately appended, jsut like the previous section. the log is not in sorted order, but it does not matter.

Storage engines that are based on this principle of merging and compacting sorted files are often called Log-structured Merge Tree(LSM) storge engine.


update-in-place storage engine
=

B-Tree
=
B-Tree keep key-value pairs sorted by key, which allows efficient key-value lookups and range queries.

The log-structured indexes we saw earlier break the database down into variable-size segments, and always write a segment sequentiallu. By contrast B-Tree break the database into fixd-size blocks ro pages, and read or write one page at a time.

B-Tree is balanced.

In memory database
=
It is faster because they do not have to encode data structure in a form that can be written to disk.

Data Warehousing
=
OLAP queries are often expensive and can harm performence. so OLTP and OLQP data base is usually separated; Data warehouse.

usually read only with analysis-friendly schema, cleanes up.(Extract-Trnasform-Load: ETL)
optimized for analysis(ex: index)




