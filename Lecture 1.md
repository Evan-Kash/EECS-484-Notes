> [!info] Course Outline
> - ^ Goal: basic introduction to database management systems
> - Two perspectives:
> 	- **<span style="color:#0070c0">External</span>**: (*Database user*)
> 		- Data models, ER model, relational model, SQL, database design
> 		- Java/JDBC Project: Common platform for building database applications
> 	- **<span style="color:#0070c0">Internal</span>** (*Database implementer*)
> 		- File organizations, access methods, sorting, concurrency control, recovery, ...
> 		- 2 projects, including a MongoDB project
> - Textbook "Database Management Systems," by Raghu Ramakrishnan & Johannes Gehrke. 3rd ed.

> [!info] Embedding SQL in a Programming Language
> - Databases are most often accessed via a declarative query language, SQL
> - SQL is usually embedded in, and called from, a traditional (procedural) programming language.'
> - Java is a common choice, and you will be using that in a project

> [!info] Overview of DBMS and Topics 
> 
> > [!info] Learning Objectives
> > - ? What is:
> > 	- A database? Why use them?
> > 	- A database schema? Example?
> > 	- Relational model?
> > 	- Entity-Relationship (ER) model
> > - ? What are the differences (if any) between:
> > 	- Conceptual schema
> > 	- Logical schema
> > 	- Physical schema 
> > 	- External schema 
> > 	- Views
> > - ? What is data independence?
> 
> > [!question] What is a DBMS?
> > - Database: large, structured collection of data
> > - A database models data of some real-world <span style="color:#0070c0">enterprise</span>
> > 	- Entities (e.g., students, courses)
> > 	- Relationships (e.g., Lisa Simpson is taking EECS 484)
> > - **<span style="color:#0070c0">DBMS: Database Management System</span>**
> > 	- A software package designed to store and manage databases
> > 	- Often (loosely) called a database
> 
> > [!warning] Flat Files
> > - Store data into a txt file
> > - ? Problems?
> > 	- Inconvenient access to data (linear operations)
> > 	- Potential data redundancy
> > 	- Integrity problems
> > 	- Atomicity problems (concurrent access issues)
> > 	- Security problems
> 
> > [!important] Why use a DBMS?
> > - It solves ALL these problems
> > 	- Data independence
> > 		- Apps need a view of the data, not info about internal representation and storage
> > 	- Efficient storage and access
> > 	- Centralized data administration
> > 	- Data integrity and security
> > 	- Concurrent access, recovery from crashes
> > 	- Reduced application dev time