> [!info] Data Models
> - **<span style="color:#0070c0">Data model</span>**: a collection of concepts for describing data
> - **<span style="color:#0070c0">Schema</span>**: a description of a particular collection of data, using a given data model
> - **<span style="color:#0070c0">Relational model</span>**: the most widely-used model today
> - **<span style="color:#0070c0">Entity-Relationship</span>** (ER) model: A "semantic" data model (i.e., a higher level more user-intuitive model)
> 	- A (relational) DBMS understands only the relational model, so we will translate an ER schema to a relational schema
> 	
> > [!example]- Relational and Other Data Models
> > - DBMS using the **<span style="color:#0070c0">relational</span>** DM ('70s-'80s)
> > 	- IBM DB2
> > 	- Informix
> > 	- Oracle
> > 	- Sybase
> > 	- Microsoft Access
> > 	- Tandem 
> > 	- Teradata 
> > 	- ...
> > - **Other data models:**
> > 	- Hierarchical (mid '60s-'70s)
> > 		- IBM IMS
> > 	- Network (70s)
> > 		- IDMS, IDS
> > 	- Object-oriented (~'90s)
> > 	- Object-relational (relational model + object DB concepts)
> > 		- Oracle
> > 	- ...

> [!info] Relational (Data) Model
> - The most widely-used model today
> 	- A collection of <span style="color:#0070c0">relations</span>
> 	- <span style="color:#0070c0">Relation</span> = set of records, naturally represented as a table with rows and (named, typed) columns
> 	- Each table row is also called a <span style="color:#0070c0">tuple</span> or <span style="color:#0070c0">record</span>
> 
>  ![[Pasted image 20240912190917.png]]
>  
> - Schema = a description of data in terms of a data model
> 	- Every relational database has a schema
> 	- Specifies the <span style="color:#0070c0">name</span> of each <span style="color:#0070c0">relation</span>, the name and type of the <span style="color:#0070c0">columns</span> 
> 
> ![[Pasted image 20240912191259.png]]

> [!info] Entity-Relationship (ER) Model 
> - A "semantic" data model
> 	- A higher-level, user-intuitive model
> - Entity-Relationship diagram:
> 	- **<span style="color:#0070c0">Entities</span>**: Student, Course
> 	- **<span style="color:#0070c0">Relationship</span>**: Enrolled_in
> 
> ![[Pasted image 20240912191447.png]]

> [!info] Levels of Abstraction 
> 
> ![[Pasted image 20240912191726.png]]
> 
> > [!example]-
> > ![[Pasted image 20240912192030.png]]

> [!info] Data Independence
> - Applications insulated from data format and storage details
> - <span style="color:#0070c0">Logical data independence</span>: protection from changes in logical structure of data
> 	- External / Logical schema interface
> - <span style="color:#0070c0">Physical data independence</span>: protection from changes in physical structure of data
> 	- Logical / Physical schema interface

> [!example] Scenario 1: Implement IMDb
> - ^ **Goal**: create IMDB
> 	- i.e., a database to store information about movies, casts directors, ratings, ...
> 
> > [!info]- ER Diagram
> > ![[Pasted image 20240912192722.png]]
> > ![[Pasted image 20240912192824.png]]
> 
> > [!info]- Scenario 1: Update
> > - <span style="color:#ef7b47">Constraint</span> (they ask you to impose it)
> > 	- A movie can have AT MOST one director
> > 	- A director can direct MULTIPLE movies
> > 
> > ![[Pasted image 20240912192920.png]]
> 
> > [!question] Types of Relationships?
> > - **<span style="color:#0070c0">Acts In</span>**: (Many-to-Many)
> > 	- An actor can act in multiple movies and a movie can have multiple actors
> > - **<span style="color:#0070c0">Directed By</span>**: (Many-to-1)
> > 	- A movie has **at most** one director
> > 	- **Arrow**: indicates **<span style="color:#0070c0">Key Constraint </span>** on directed-by relationship: a movie in the relationship must be unique
> > 
> > ![[Pasted image 20240912193309.png]]
> 
> > [!info]- Scenario 1: Update (2)
> > ![[Pasted image 20240912194148.png]]
> > - **<span style="color:#ef7b47">Constraint 2</span>**
> > 	- Every Movie entity must participate in a relationship with an Actor
> > 		- i.e., every movie must have ***at least*** one actor
> 
> > [!info] Participation Contraints
> > - **Heavy line**
> > 	- ![[Pasted image 20240912193612.png]]
> > 	- Every Entity-1 entity **must participate** in a relationship with an Entity-2 entity
> > - Light line 
> > 	- An Entity-2 can be related to $\geq 0$  Entity-1 entities
> 
> > [!info] Final ER Diagram
> > ![[Pasted image 20240912193806.png]]
> 
> > [!example]- Child and Birth Mother Example
> > ![[Pasted image 20240912193906.png]]
> > 
> > - **Key** Constraint:
> > 	- A child has **at most** one birth mother but a birth mother may bear several children
> > - **Participation** Constraint:
> > 	- Each child must have **at least** one birth mother
> > - **Net Result**: Every child has exactly one birth mother
> 
> > [!info]- Scenario 1: Update (3)
> > ![[Pasted image 20240912194109.png]]
> > 
> > - Actors & directors have attributes: ID, Name, DOB
> > - Movies have attributes: ID, title, year, type
> 
> > [!example]- Diagram: Attributes
> > ![[Pasted image 20240912194251.png]]

> [!info] Keys
> ![[Pasted image 20240912194413.png]]
> 
> - **<span style="color:#0070c0">Candidate keys</span>**: potential keys
> - Students in a student database have multiple **potential keys** (they must be unique to be a key)
> 	- Student ID
> 	- Login name 
> 	- SSN
> 	- (Name, address)
> 
> > [!info] Primary Key
> > - **Primary Key**: one of the candidate keys
> > - The primary key attribute(s) is (are) <u>underlined</u> in the ER diagram
> > - When you design a database, the **primary** key is **cross-referenced** in other tables to represent relationships
> > 	- & E.g., For students, <span style="color:rgb(255, 0, 0)">Student ID</span> is a good primary key
> 
> ![[Pasted image 20240912194938.png]]

> [!info] Modeling Problem
> ![[Pasted image 20240913165043.png]]
> 
> - **Exercise**
> 	1. Identify entities (objects), relationships between entities
> 	2. Attach attributes
> 	3. Keys: something that uniquely identifies an entity
> 
> > [!info]- Add in The Relationships
> > ![[Pasted image 20240913165320.png]]
> > 
> > - **Relationship set:** $\{ (e_1, \cdots, e_n)\} \space | \space e_1 \in E_1, \cdots,\, e_n \in E_n$
> > 	- & E.g., $\text{Vote: } \{(c_1, p, i), (c_2, p, i), \cdots\}$
> > - **Entity sets:** Collection of entity instances
> > 	- & E.g., a set of citizens
> > 
> > ![[Pasted image 20240913165730.png]]
> > 
> > ![[Pasted image 20240913165857.png]]

> [!info] Advanced ER
> 
> > [!info]- Additional Requirement 1
> > ![[Pasted image 20240913170222.png]]
> > 
> > - <span style="color:rgb(239, 123, 71)">Suppose we want to also record *when* a Citizen voted</span> 
> > - ? How should we represent that?
> > 
> > > [!info] Attributes on Relationships
> > >  ![[Pasted image 20240913170301.png]]
> 
> > [!info]- Additional Requirement 2
> > ![[Pasted image 20240913173006.png]]
> > 
> > > [!info]- Key Constraints
> > > - ? Relationship between Citizen and PR-Cand?
> > >   
> > > ![[Pasted image 20240913173143.png]]
> > > 
> > > > [!info] Generalize
> > > > ![[Pasted image 20240913173218.png]]
> 
> > [!info]- Additional Requirement 3
> > ![[Pasted image 20240913173340.png]]

> [!info] Weak Entities
> ![[Pasted image 20240913173427.png]]
> 
> - A **<span style="color:rgb(0, 112, 192)">weak entity</span>** can be identified only by considering *some of its attributes in conjunction with the primary key* of the another entity (**identifying owner**)
> - **Rules**:
> 	- Weak entity has single owner (**one-to-many relationship**)
> 	- Weak entity must have **total participation** in the above identifying relationship set

> [!info] ISA ('is a') Hierarchies
> - Attributes are inherited (as in C++)
> - If A <span style="color:rgb(0, 112, 192)">ISA</span> B, every A entity is also a B entity
> - Specialize superclass (top-down design)
> - Generalize subclasses (bottom-up design)
>   
> ![[Pasted image 20240913173748.png]]
> 
> - Do not overuse them!
> - Constraint types:
> 	- ? **Overlap:** Can $\geq$ 2 subclasses contain the same entity?
> 		- Overlapping vs. Disjoint (default)
> 	- ? **Covering:** Do the entities in the subclasses include ALL the entities in the superclass?
> 		- & I.e., union of subclass entities = the set of superclass entities?
> 			- Total vs. Partial (default)

> [!info] Relationships with Relationships
> - Each **Project** must be sponsored by at least one **Department**
> - Each **sponsoring relationship** must be monitored by exactly one **manager**
>   
> ![[Pasted image 20240913174923.png]]
> 
> ![[Pasted image 20240913174715.png]]
> 
> > [!info]- Aggregation
> > - More complete example
> > - Each **sponsoring relationship** must be monitored by exactly one **manager**
> > 
> > ![[Pasted image 20240913180420.png]]

> [!info] Choosing among available ER concepts
> 
> > [!info] Conceptual Design Using the ER Model
> > 
> > - Design choices:
> > 	1. Model a concept as an **entity** or an **attribute**?
> > 	2. Model a concept as an **entity** or an **attribute**?
> > 	3. **Binary** or **ternary** relationship? **Aggregation**?
> > 
> > > [!info]- Entity vs. Attribute
> > > - Address of a Party: entity or attribute?
> > > - Go with **entity** IF you want to:
> > > 	- Store several addresses per Party
> > > 	OR
> > > 	- Encode the structure of the address (city, street, etc.)
> > > 	  
> > > ![[Pasted image 20240913180836.png]]
> > > 
> > > - ? Can employee work in a given dept. for two or more periods?
> > >   
> > > ![[Pasted image 20240913180916.png]]
> > 
> > > [!info]- Entity vs. Relationship
> > > - Manager (also an employee gets a separate discretionary budget for each dept.)
> > > - ? What if we want Manager to get a discretionary budget that covers <span style="color:rgb(239, 123, 71)">all</span> managed depts?
> > > 	- **<span style="color:rgb(0, 112, 192)">Redundancy</span>** of dbudget, in each Manages2 relationship
> > > 	- **<span style="color:rgb(0, 112, 192)">Misleading</span>**: suggests dbudget tied to relationship, not mngr 
> > > 	  
> > > > [!success]- One Solution
> > > > ![[Pasted image 20240913181515.png]]
> 
> > [!question]- Participation Constraint in a Ternary Relationship?
> > - A citizen votes at most once and at only one polling location (on a specific date)
> >   
> >  ![[Pasted image 20240913181642.png]]
> 
> > [!example]- Try it Out!
> > ![[lec02-ER.pptx (dragged).pdf]]
> 
> > [!important] Summary of Conceptual Design
> > - High-level description of data to be stored
> > - ER model popular for conceptual design
> > 	- Constructs are expressive and natural 
> > 	- Basic constructs: **entities, relationships, and attributes** (of entities and relationships)
> > 	- Additional constructs: **weak entities, ISA, aggregation.**
> > 	- Integrity constraints: **key constraints and participation constraints**
> > - ^ Note: There are many variations on ER model
> > - ER designing is subjective