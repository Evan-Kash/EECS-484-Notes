> [!abstract] Databases "In the Wild"
> - So far, we've talked about the DBMS as a standalone system
> 	- Access interactively by writing SQL queries (e.g., using SQL\*Plus)
> - In practice, DBMS is often part of a larger software infrastructure
> 	- Multi-tiered system architecture
> 	- Access database from another program


> [!info] Database "Ecosystem" (1)
> - Client-Server Architecture
> 
> ![[Pasted image 20240929223930.png]]
> 
> > [!info]- Many Clients
> > ![[Pasted image 20240929223950.png]]

> [!info] Database "Ecosystem" (2)
> - "3-Tier Architecture" (common to add more tiers, too)
> 
> ![[Pasted image 20240929224031.png]]

> [!info] Embedding SQL in Application
> ![[Pasted image 20240929224052.png]]
> 
> > [!info]- SQL Integration with PL
> > - ? **Problem**: What is the interface between SQL and programming language
> > - **A popular solution**
> > 	- "Embed" SQL in host language
> > 	- Provide an API for processing query results
> > - We will see one such example next for Java
> > - Similar embeddings of SQL exist for Python and other popular languages
> 

> [!info] JDBC ("Java-Database Connectivity")
> ![[Pasted image 20240929224319.png]]
> 
> > [!info]- Connections
> > - Get Connection object:
> > 	- Oracle requires passwords
> > 	- Sqlite3 is file-based and does not require a password
> > - Always close connections before quitting the program
> > 	- `conn.close()`
> > 	- Similarly, close other Oracle resources
> 
> > [!info]- JDBC - AutoClose Trick
> > ![[Pasted image 20240929224612.png]]
> 
> > [!warning]- Challenges
> > - DBMS and PL implement different data types
> > 	- "Impedance Mismatch"
> > - Need to match DB types with PL types, e.g.,
> > - ? What computation to do in the database vs. the application program?
> > 	- Rules of Thumb:
> > 		- Avoid fetching more data than necessary
> > 		- "Push" data processing to the DBMS when possible
> > 		  
> > ![[Pasted image 20240929224720.png]]
> 
> > [!info]- Stored Procedures and UDFs
> > ![[Pasted image 20240929225257.png]]
> > 
> > > [!info] Set Functions/Stored Procedures
> > > ![[Pasted image 20240929231534.png]]
> 
> > [!info]- `PreparedStatement`
> > - Statement (Base class)
> > 	- Arbitrary SQL query
> > 	- DBMS parses and optimizes each query
> > - PreparedStatement
> > 	- Parameterized SQL query
> > 	- DBMS "pre-compiles" the query (parses, optimizes, and stores query execution plan)
> > 	- Can be sued multiple times
> > 	- Amortizes optimization cost across multiple uses
> > 
> > > [!info]- Statement vs. PreparedStatement
> > > ![[Pasted image 20240929231722.png]]
> > 
> > - PreparedStatement also does some type checking on parameters and removal of escape characters
> > - Helpful for preventing some security problems (e.g., SQL Injection)
> 
> > [!info]- Security Issues / SQL Injection
> > - Common vulnerability in database applications
> > 	- SQL injection is simple, yet surprisingly common
> > 	- Can be prevented with defensive coding
> > 	  
> >![[Pasted image 20240929231920.png]]
> >
> > > [!example]- SQL Injection - Example
> > > ![[lec07-dbApp.pptx (dragged) 2.pdf]]
> > 
> > > [!info] Prevention #1 - Sanitize
> > > - **Check and sanitize any untrusted inputs**
> > > - E.g., any browser input is fundamentally untrusted and potentially malicious
> > > - So, sanitize before inserting into query so that an unauthorized sql query cannot be injected
> > 
> > > [!info]- Weird Password Rules
> > > ![[Pasted image 20240929232233.png]]
> > 
> > > [!info]- Prevention #2 - Always Use PreparedStatement
> > > ![[Pasted image 20240929232335.png]]
> > 
> > > [!info]- Prevention #3 - DB Access Control
> > > - Limit JDBC app's rights by assigning it low-privilege account (just enough for it to get its work done)
> > > 	- Most DBMSes allow restricting read/write access to tables or columns (and sometimes rows) based on user id
> > > 	  
> > > 	![[Pasted image 20240929232504.png]]
> > > 	
> > > - Views can also help restrict access
> > 
> > > [!info]- Prevention #4: Encryption
> > > - At-rest encryption: prevents data loss if disk or computer gets stolen. But, data in plaintext at run-time
> > > - Encrypted databases such as CryptDB and Mylar: Data kept encrypted. Queries also encrypted

> [!example]- JDBC Example
> ![[lec07-dbApp.pptx (dragged).pdf]]


> [!important] Summary
> - DBMS is often part of a larger software infrastructure
> 	- & E.g., Database-backed web applications
> - Integrating SQL with application code is a messy problem
> 	- Efficiency: push computation "close" to data
> 	- Security: sanitize input and other defenses