> [!question] Why Go Beyond Textbook?
> - What we teach in 484
> 	- Concepts, techniques, and ideas
> - What we do NOT teach in 484
> 	- Specific tools and technologies
> - ? Why are we teaching this lecture?
> 	- With 484 concepts, you can easily learn state-of-the-art
> 	- Prepare yourself for the job market
> 	- Understanding where the DB industry is headed

> [!important] Overview
> - Traditional RDBMS
> 	- Most of the focus of this course
> - Modern RDBMS (performance improvement strategies, based on workload) - may get to some of this in part 2 of the course
> - NoSQL
> 	- Key-value stores
> 	- Document stores
> 	- **MapReduce**

> [!info] NoSQL
> - **Key observation**: <u>not every</u> data problem is best solved by traditional relational databases
> - NoSQL = No SQL = Not using <span style="color:rgb(0, 112, 192)">traditional RDBMS</span> 
> 	- NoSQL $\neq$ Not using SQL language!
> 	- NoSQL = Not Only SQL
> 		- They may still support SQL language
> 			- & E.g., Hive
> 
> > [!info] Traditional RDBMS vs. NoSQL
> > - A DBMS provides: <span style="color:rgb(0, 112, 192)">**efficient**</span>, <span style="color:rgb(0, 112, 192)">**reliable**</span>, <span style="color:rgb(0, 112, 192)">**convenient**</span>, and <span style="color:rgb(0, 112, 192)">**safe multi-user**</span> storage of and access to <span style="color:rgb(0, 112, 192)">**massive**</span>  amounts of **<span style="color:rgb(0, 112, 192)">persistent</span>** data
> > 
> > ![[Pasted image 20241007205138.png]]

> [!info] Distributed Hash Tables
> - Given the key, find value
> - Hash table itself os big, and we don't want to centralize the lookup (can become a bottleneck)
> - Partition the hash table, and distribute across multiple nodes
> - Query comes into some node, and is redirected to the correct one (possibly multiple hops)
> 
> > [!info] Key-Value Stores
> > - Simples type of Data Model: <span style="color:rgb(0, 112, 192)">(key, value)</span> pairs
> > 	- & Ex: <span style="color:rgb(0, 112, 192)">Redis, Amazon DynamoDB, Azure Cosmos DB, RocksDB</span>
> > 	- Value can be a binary string, ...
> > 	- API: <span style="color:rgb(0, 112, 192)">get</span>(key), <span style="color:rgb(0, 112, 192)">put</span>(key, value), <span style="color:rgb(0, 112, 192)">delete</span>(key)
> > - **Wide Column Stores**: support tables by storing
> > 	- (Key, columnName, value) triplets
> > 	- Unlike a relational DB, the names and format of the columns can vary from one row to another within the same table
> > 		- & Ex: <span style="color:rgb(0, 112, 192)">Cassandra, BigTable, HBase</span>
> > 
> > > [!info]- Wide Column Stores
> > > - Use one (eky, columnName, value) triple per logical column in a logical record
> > > - Not al columns are required in all records. Schema-free
> > > - Typically, very large number of columns (possibly millions)
> > > - & Ex: <span style="color:rgb(0, 112, 192)">Cassandra, BigTable, HBase, .... Figure below from the Google’s BigTable paper</span> 
> > > 
> > > ![[Pasted image 20241007205815.png]]
> 
> > [!info] Document Stores
> > - Data model: <span style="color:rgb(0, 112, 192)">(key, document)</span> pairs
> > - <span style="color:rgb(0, 112, 192)">Document:</span> JSON format typically (or XML in some)
> > - In addition to lookup by key, they can also fetch documents by their content
> > - & Ex: MongoDB, CouchDB, DynamoDB (as well), DataBricks
> > - Can use multiple servers via <span style="color:rgb(255, 0, 0)">sharding</span> 
> > - The DBMS provides a distributed hash table (DHT) - which allows lookup of a document given a key
> 
> > [!info]- Case Study: MongoDB Documents
> > - Document corresponds to a tuple in a relation
> > 
> > ![[Pasted image 20241007210418.png]]
> > 
> > - Documents are simply JSON objects in JavaScript syntax, consisting of **field:value** pairs
> > - Documents can be hierarchical - a value can be a JSON object or a list
> 
> > [!info]- Case Study: Mongo DB Collections
> > - A collection corresponds to a table in relational databases.. It is a set of documents (common structure among documents in the same collection is **NOT** enforced)
> > 
> > ![[Pasted image 20241007210604.png]]
> 
> > [!info] Key Commands in MongoDB
> > - `db.colelctionname.insert(json_object)`
> > - `db.collectionname.find(predicate)`
> > - http://docs.mongodb.org/manual/tutorial/getting-started/
> >   
> > > [!example] Example
> > > <h3>Setup</h3>
> > > 
> > > ![[Pasted image 20241007210809.png]]
> > > 
> > > <h3>Queries</h3>
> > > 
> > > ![[Pasted image 20241007210819.png]]
> > > 
> > > <h3>Iterate Over a Cursor</h3>
> > > 
> > > ![[Pasted image 20241007211026.png]]
> > > 
> > > <h3>Selections: Predicates in Find</h3>
> > > 
> > > ![[Pasted image 20241007211100.png]]
> > > 
> > > <h3>Projections</h3>
> > > 
> > > ![[Pasted image 20241007211209.png]]
> > > ![[Pasted image 20241007211235.png]]
> > > 
> > > <h3>Counting</h3>
> > > 
> > > ![[Pasted image 20241007211324.png]]
> 
> > [!info] Aggregations -- Pipeline
> >  ![[Pasted image 20241007211422.png]]
> > 
> > > [!info] Other Aggregate Stages
> > > ![[Pasted image 20241007211409.png]]
> 
> > [!info] MapReduce
> > - MapReduce system provides:
> > 	- Automatic parallelization & distribution
> > 	- Fault-tolerance
> > 	- Status & monitoring tools
> > 	- Clean abstraction for programmers
> > 
> > > [!info]- Data-Centric Programming
> > > - MapReduce has become very popular, for lots of good reasons
> > > 	- Easy to write distributed programs
> > > 	- Built-in reliability on large clusters
> > > 	- Bytestreams, not relations
> > > 	- "Schema-later", or "schema-never"
> > > 	- Your choice of programming languages
> > > 	- Hadoop relatively easy to administer
> > 
> > - Many data programs can be written as *map* and *reduce* functions
> > - `Map` transforms ***key, value*** inputs into new ***key', value'***
> > 	- `Map(k, v) => (k', v') list`
> > - `Reduce` receives all the values for a given key' and can output to disk file
> > 	- `Reduce(k', v' list) => (out-key, out-val) list`
> > 
> > ![[Pasted image 20241007211920.png]]
> > 
> > > [!info]- Execution Pipeline
> > > - MapReduce consists of 2 main stages:
> > > 	- `Map`
> > > 	- `Reduce`
> > > - In stage 1, partition input data and run **`map()`** on many machines 
> > > - Then group intermediate data by key 
> > > - In stage 2, partition data by key and run **`reduce()`** on many machines
> > > - Output is whatever `reduce()` emits
> > 
> > > [!info]- Processing Large Data
> > > - Many CPUs needed. 1000s, not dozens
> > > 	- Programmer cannot know how many machines at program-time
> > > 	- Job is very long-lasting
> > > 	- Machines die, machines depart; job must survive
> > > - Map/Reduce architecture makes it possible to handle all the above without burdening the programmer