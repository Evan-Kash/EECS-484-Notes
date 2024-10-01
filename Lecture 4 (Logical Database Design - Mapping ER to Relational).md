> [!info] Recall ER Constructs
> - Basic Constructs
> 	- Entity sets
> 	- Relationship Sets
> 	- Attributes (of entities and relationships)
> - Additional Constructs
> 	- ISA Hierarchies
> 	- Weak Entities
> 	- Aggregation
> - Integrity Contraints
> 	- Key constraints and Participation constraints
> 	- ISA hierarchies

> [!info] Entity Sets to Tables
> 
> ![[Pasted image 20240914145146.png]]
> 
> - ? Can `cid` be NULL?
> 	- $ No

> [!info] Relationship Sets to Tables
> ![[Pasted image 20240914145257.png]]
> 
> - ^ Note that you need to specify the cid column in REFERENCES
> - Foreign key: keys from participating entity sets
> - Descriptive attributes
>   
> ![[Pasted image 20240914145453.png]]

> [!info] Key Constraints
> ![[Pasted image 20240914145535.png]]
> 
> - Notice the arrow from Citizens to Votes
> 
> > [!info]- Approach 1: Key Constraint
> > - Three tables (Citizens, Votes, Initiative). Vote table change
> >   
> > ![[Pasted image 20240914145630.png]]
> 
> > [!info]- Approach 2: Key Constraint
> > - Only two tables: Citizen_votes and Initiative tables 
> > 
> > ![[Pasted image 20240914145723.png]]
> 
> > [!question]- Which Approach is Better?
> > 
> > ![[Pasted image 20240914145756.png]]
> 
> > [!question]- What About Folding Everything Into One Table?
> > - ! No! This is a bad design
> > 	- & E.g., for every citizen that votes for Initiative A, we have to store iname, idesc information → REDUNDANCY
> 
> > [!example]- N-ary Relationship Example
> > 
> > ![[Pasted image 20240914150458.png]]

> [!info] Participation Constraints
> ![[Pasted image 20240914150553.png]]
> 
> > [!question]- Try Approach 1?
> > 
> > ![[Pasted image 20240914150724.png]]
> 
> > [!info]- Mapping Participation Constraints (1-to-1)
> > 
> > ![[Pasted image 20240914150810.png]]
> 
> > [!info] Participation Constraints Only
> > ![[Pasted image 20240914151249.png]]
> > - ? Try Approach 2?
> > 	- Doesn't work since a Citizen can vote multiple times
> > - ? Try Approach 1?
> > 	- Citizens table, Votes table, Initiative Table
> > 	- ? How to guarantee that every Citizen appears in the Votes table?
> > 	- Unfortunately, this is hard to enforce in SQL. Requires multi-table constraints, which are usually not supported in DBMSes
> > 	- **Typical Practical Solution:** Ignore participation-only constraints - don't bother enforcing them in the database
> > 		- **Use Approach 1**
> 
> > [!info] Weak Entities
> > - Use Approach 2: Combine weak entity and owning relationship into one relation
> > 	- <span style="color:rgb(0, 112, 192)">Delete all weak entities when an owner entity is deleted</span>
> > 	
> > ![[Pasted image 20240914151341.png]]

> [!info] ISA Hierarchies: General Approach 
> - Three relations:
> 	- Citizens(<u>ssn</u>, name, bday)
> 	- PR-Cands(<u>ssn</u>, waddr, budget)
> 	- President(<u>ssn</u>, from, to)
> 	- Add foreign key constraints
> - Queries:
> 	- Involving all Citizens → Easy
> 	- Involving just PR-Cands → may need to <span style="color:rgb(255, 0, 0)">join</span> PR-cands with Citizens to get the needed attributes

> [!info] Aggregation - E.g., Monitors
> 
> ![[Pasted image 20240914151638.png]]


> [!example] Exercise
> 
> > [!example]- ER Diagram
> >  ![[Pasted image 20240914151846.png]]
> > 
> > ![[Pasted image 20240914151859.png]]
> 
> > [!example]- SQL DDL
> > - Write SQL statements to create the corresponding relations, and to capture as many of the constraints as possible
> >   
> > ![[Pasted image 20240914152811.png]]

> [!info] Integrity Constraints
> - Describe conditions that must be satisfied by every legal instance
> - Types of integrity constraints
> - Foreign key constraints
> - <span style="color:rgb(0, 112, 192)">General contraints</span> 

> [!info] Table Constraints
> - More general than key constraints
> - Can use a query to express constraint
> 	- Constraints checked each time a table is updated
> 	- CHECK constraint always true for empty relation
> 
> ![[Pasted image 20240914155806.png]]
> 
> > [!example]- Trying it In SQLPLUS or SQLite or duckDB
> > ![[Pasted image 20240914155944.png]]
> > 
> > ![[Pasted image 20240914155950.png]]
> 
> > [!info]- More General CHECKs
> > - SQL standard allows cross-table CHECK constraints
> > - <span style="color:rgb(239, 123, 71)">But they are not supported in most systems - expensive to enforce</span>
> > - <span style="color:rgb(239, 123, 71)">Thus, we will not worry about them</span>

> [!info] Active Databases & Triggers
> ![[Pasted image 20240914160128.png]]
> 
> - Three parts:
> 	- Event (activates the trigger)
> 	- Condition (test that is run when trigger is activated)
> 	- Action (what happens if the trigger runs)
> 		- Before and After Triggers
> - Trigger Execution:
> 	- Row-level Triggers: Once per modified row
> 	- Statement-level Triggers: Once per SQL statement 
> 
> > [!example]- Log Entries
> > ![[Pasted image 20240914160306.png]]
> > 
> > ![[Pasted image 20240914160313.png]]
> > 
> > ![[Pasted image 20240914160321.png]]
> 
> > [!info]- Triggers 
> > - When a condition is checked, success/failure can be used to trigger arbitrary actions
> > - Used for many things:
> > 	- Check complex actions (such as credit limit in a shopping application)
> > 	- Generate logs for auditing and security checks
> 
> > [!info]- Recall CASCADE Constraints
> > ![[Pasted image 20240914160506.png]]
> > 
> > > [!info] CASCADE Using Triggers
> > > ![[Pasted image 20240914160528.png]]
> 
> > [!info] Trying Out Triggers
> > - Try out the file <span style="color:rgb(0, 112, 192)">athlete_trigger_casacde.sql</span> in sqlplus
> > - Also try it out in sqlite to see if it supports triggers in the same way
> > - Try removing a row from athlete. Does it cascade to compete via the trigger?
> > - Try dropping the trigger?
> > 	- `DROP TRIGGER triggername`
> > - ? What happens now on deleting a row from Athlete
> 
> > [!important] Triggers: Pitfalls and Pain
> > - Triggers can be recursive!
> > 	- Chain of triggers can be hard to predict, which makes triggers difficult to understand and debug
> > - Errors with "mutating" table
> > 	- A table that is currently being modified by an UPDATE, DELETE, or INSERT statement, or a table that might be updated by the effects of a DELETE CASCADE constraint
> > 	- The session that issued that triggering statement cannot query or modify a mutating table
> > 	- Used to prevent a trigger from seeing **inconsistent data**