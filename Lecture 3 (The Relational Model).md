> [!info] Relational (Data) Model
> - **Schema**: a description of data in terms of a data model 
> - **Instance**: a table, with rows (aka tuples, records), and columns (aka fields, attributes) that match the schema
> 	- Number of rows: cardinality
> 	- Number of columns: degree or arity
> 
> ![[Pasted image 20240913212154.png]]

> [!example] New Scenario: Olympic Games
> 
> > [!example]- Instance of Athlete Relation 
> > 
> > ![[Pasted image 20240913212501.png]]
> > 
> > - ? What is this schema?
> > 
> > ![[Pasted image 20240913212519.png]]
> 
> 
> > [!info] Relational Query Language
> > - Supports simple, powerful, <span style="color:rgb(0, 112, 192)">querying</span> of data
> > - Queries written <span style="color:rgb(0, 112, 192)">declaratively</span>
> >	- In constrast to <span style="color:rgb(0, 112, 192)">procedural</span> methods
> > - DBMS is responsible for <span style="color:rgb(0, 112, 192)">efficient evaluation</span>
> >	- System can optimize for <u>efficient query execution</u>, and still ensure that <u>answer does not change</u>
> > - SQL is the standard database query language
> >  
> >   ![[Pasted image 20240913212902.png]]
>
> > [!info] Create a Table (Relation)
> > 
> > ![[Pasted image 20240913213007.png]]
> > 
> > ![[Pasted image 20240913213204.png]]
> > 
> > > [!info]- Creating Relations in SQL
> > > ![[Pasted image 20240913213456.png]]
> > > 
> > > - Create the athlete relation
> > > 	- Domain constraint (type) enforced when tuples added or modified
> > > - Create the Olympics relation
> > > - Create the Complete relation
> > 
> > > [!info] Integrity Contraints (ICs)
> > > - Must be true for *<span style="color:rgb(0, 112, 192)">every</span>* instance of the database
> > > 	- ICs are specified when schema is defined
> > > 	- ICs are checked whenever relations are modified
> > > - A <span style="color:rgb(0, 112, 192)">legal</span> instance of a relation satisfies \*all\* specified ICs
> > > 	- DBMS must not admit illegal instances


> [!example] Example Integrity Contraint
> - Specify certain attributes as <span style="color:rgb(0, 112, 192)">keys</span> of a table 
> - Reference keys of entities in other tables
> - No dangling references are allowed in a database when updates occur to any table 
> 
>  ![[Pasted image 20240913214138.png]]
>  
> > [!info]- Primary Key Constraint
> > 
> > ![[Pasted image 20240913214532.png]]
> 
> > [!info]- Not Null Constraint
> > - & Example: Disallow null values for name attribute:
> > 
> > ![[Pasted image 20240913214557.png]]
> > 
> > - **NULL** value implies the value is unknown or inapplicable
> > - Country and sport can be NULL (unspecified)
> > - But, name must be specified
> 
> > [!info]- Primary Keys Properties
> > - SQL Standard: 
> > 	- A primary key attribute cannot be null
> > - Primary key often an integer ID for efficiency
> > - **Design consideration**: Primary keys should be long-term stable, unique, and ideally, not sensitive. Avoid addresses, SSN, etc.
> 
> > [!info]- Candidate Keys
> > - Candidate keys specified as <span style="color:rgb(0, 112, 192)">UNIQUE</span>
> > - One of the candidate keys is chosen as the *primary key*
> > 
> > ![[Pasted image 20240913215113.png]]
> > 
> > - Unique attributes can be NULL, unless NOT NULL is specified
> > 	- <span style="color:rgb(0, 112, 192)">Only the NON-NULL attribute values need to be UNIQUE</span>
> 
> > [!info]- Foreign Keys in SQL
> > - Complete table has relationships between athletes in the Athlete table and the olympics in the Olympics Table
> > 
> > ![[Pasted image 20240913215355.png]]
> > 
> > ![[Pasted image 20240913215414.png]]
> 
> > [!info] Sample Database
> > ![[Pasted image 20240913215449.png]]

> [!info] Enforcing Integrity Constraints
> 
> > [!info]- Enforcing Referential Integrity
> > 
> > - If a Complete tuple is <span style="color:rgb(0, 112, 192)">inserted</span> with no corresponding Athlete aid:
> > 	- Insert operation is REJECTED
> > 	  
> > ![[Pasted image 20240913223832.png]]
> > 
> > - ? What if an Athlete tuple is deleted?
> >  
> >  > [!success]- Integrity Enforced in SQL Standard on DELETE/UPDATE
> >  > - NO ACTION (also called RESTRICT): disallow action (default)
> >  > - CASCADE: also delete all referencing tuples
> >  > - SET NULL / SET DEFAULT: sets foreign key value of referencing tuple to NULL or a default value
> >  > 
> >  > ![[Pasted image 20240913224228.png]]
> >  
> 
> > [!question]- Where do ICs Come From?
> > - Based on real-world enterprise being modeled
> > - An IC is a statement about <span style="color:rgb(0, 112, 192)">all</span> possible instances!
> > - ^ We can **check** a database instance to see if an IC is **violated**, but we can <span style="color:rgb(0, 112, 192)">NEVER</span> infer that an IC is true by looking at an instance
> > - Key and foreign key ICs are the most common
> 
> > [!info] Destroying & Altering Relations
> > - To destroy the relation Olympics
> > 	- Schema information and tuples are deleted
> > 
> > 	![[Pasted image 20240913224522.png]]
> > 	
> > - To alter the Athlete schema by adding a new column
> >   
> > 	![[Pasted image 20240913224551.png]]
> > 
> > - ? What do we put in the new field?
> > 	- A <span style="color:rgb(0, 112, 192)">null</span> value: 'unknown' or 'inapplicable'

> [!important] Relational Model: Summary
> - A tabular representation of data
> - Simple and intuitive
> - The most widely used database model by far
> - Integrity constraints can be specified by the DBA, based on application semantics. DBMS checks for violations
> 	- Two important ICs" <u>primary</u> and <u>foreign</u> keys
> 	- We <u>always</u> have domain constraints
> 		- & E.g., `INTEGER` fields must always contain integer values
> - Views can be used for external schemas, and provide logical data independence