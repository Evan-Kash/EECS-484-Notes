> [!abstract]- Review
> ![[Pasted image 20240930054625.png]]

> [!important]- Today
> ![[Pasted image 20240930054641.png]]

> [!info] Form/Spreadsheet
> ![[Pasted image 20240930054736.png]]
> - ! Bad Table!
> 	- (Supplier ID, item) appears to be key, but Supplier ID is NULL in many places - assumed to copied from the prior non-null entry - ordering matters
> 	- Addresses appear to be multi-valued
> 	- Redundancy in (Item, Desc)
> 
> > [!info] Normalization
> > - Going to a proper set of tables is called "normalization"
> > 	- Avoid redundancy of data
> > 	- Capture the dependencies inherent in the data
> > - We will always start with one giant table and then "normalize it" into multiple tables, ala, P1

> [!info] Normalization
> 
> > [!important]- Goal
> > - Design 'good' tables
> > 	- ? What is good?
> > 	- ? How to fix bad tables?
> > - In short:
> > 	- ^ We want tables where the attributes depend on the primary key, the **whole** key, and **nothing but** the key
> 
> > [!info]- Two Approaches to Normalization
> > - Approach 1 (P1):
> > 	- Create an ER model and then map tables. Should result in good (normalized) tables (very manual)
> > - Approach 2 (Today):
> > 	- State dependencies between attributes of tables
> > 	- MaP dependencies to tables. Can be done automatically
> 
> > [!info] Normal Forms
> > - Guarantees that certain problems won't occur & obeys certain rules:
> > 	- 1 NF: Starting point
> > 	- 2 NF: Historical
> > 	- 3 NF: $\cdots$
> > 	- BCNF: Boyce-Codd Normal Form
> > 	- 4NF: Use lossless decompositions for multi-valued dependencies
> > 
> > > [!info]- 1st Normal Form - First Step
> > > ![[Pasted image 20240930055456.png]]
> > > 
> > > - Each value in table is single-valued
> > > - Each row contains all the relevant data
> > > - We know have a relational table, rows can be reordered and are all independent
> > > <br>
> > > - Redundancy remains however
> > > 
> > > ![[Pasted image 20240930055654.png]]
> > 
> > > [!info]- Redundancy Bad for Changing DBs
> > > - Space inefficient - same thing stored multiple times
> > > - Makes for messy update process
> > > 	- **Update anomalies**: changing address of a supplier requires changes multiple rows
> > > 	- **Insertion anomalies**: inserting a supplier requires inserting NULL or other values in unrelated columns
> > > 	- **Deletion anomalies**: deleting an item requires care, it could end up deleting a supplier as well
> > > 
> > > > [!info] Dealing with Redundancy
> > > > - Normalize tables further
> > > > - ER diagramming and translation to Relational model did that
> > > > - But ER diagramming and translation seems a bit ad hoc. Can the method be formalized?
> > > > - We will learn another trick today: using <span style="color:rgb(239, 123, 71)">functional dependencies</span> more to normalize tables
> > > > 
> > > > > [!example]- Normalization using ER Approach
> > > > > ![[Pasted image 20240930060145.png]]
> > > > 
> > > > > [!example]- Alternative Way: Use Functional Dependencies
> > > > > ![[Pasted image 20240930060217.png]]
> > 
> > > [!info]- Functional Dependencies
> > > - FD captures dependency between attributes
> > > - Notation: $X \rightarrow Y$
> > > - Read as: X functionally determines Y
> > > 	- & i.e., *Y depends on X or for a given X, there is one Y*
> > > 
> > > ![[Pasted image 20240930060423.png]]
> > > 
> > > > [!info] FD: Definiton
> > > > - Notation: $X \rightarrow Y$
> > > > - **Informally**: given a specific X, there is one Y value
> > > > - **Formally**: a form of Integrity Constraint
> > > >   
> > > > ![[Pasted image 20240930060511.png]]
> > > 
> > > > [!example]- Example
> > > > ![[Pasted image 20240930060656.png]]
> > > 
> > > > [!tip]- More on FDs
> > > > ![[Pasted image 20240930060756.png]]
> > 
> > > [!info]- Basic Normalization
> > > ![[Pasted image 20240930060824.png]]
> > > 
> > > > [!example]-
> > > > ![[Pasted image 20240930060858.png]]
> 
> > [!info]- High-Level Goal
> > ![[Pasted image 20240930060943.png]]
> 
> > [!info]- Concept of Closure
> > - Given:
> > 	- A base set of "facts"
> > 	- A set of derivation rules
> > 	- Closure is the set of all derivable facts
> > 
> > ![[Pasted image 20240930061044.png]]
> 
> > [!info]- Implied FDs
> > <span style="color:rgb(239, 123, 71)">F+: Closure of F</span> = Set of all valid FDs
> > 
> > ![[Pasted image 20240930061126.png]]
> > 
> > - Many other dependencies in the closure F+, e.g.,
> > 	- Supplier ID, Item → Desc
> > 	- Supplier ID → Supplier ID
> > 	- Supplier ID → Supplier ID, Supplier Name
> > - How to derive F+: Armstrong's Axioms!
> 
> > [!info]- First Armstrong Axioms
> > ![[Pasted image 20240930061430.png]]
> > <br>
> > ![[Pasted image 20240930061407.png]]
> > 
> > > [!info] Sound and Complete
> > > ![[Pasted image 20240930061514.png]]
> 
> > [!info]- Solution to Redundancy: Decomposition
> > ![[Pasted image 20240930061550.png]]
> > - Two key goals of decomposition:
> > 	- <span style="color:rgb(0, 112, 192)">Lossless Join</span>: can we reconstruct the original relation from instances of the decomposed relations?
> > 	- <span style="color:rgb(0, 112, 192)">Dependency Preservation</span>: avoid having to join decomposed relations to check dependencies
> > - Downside of decomposition:
> > 	- <span style="color:rgb(0, 112, 192)">Some queries</span> become <span style="color:rgb(0, 112, 192)">more expensive</span> (more joins)
> 
> > [!info]- Lossless Join Decompositions
> > ![[Pasted image 20240930061807.png]]
> > 
> > > [!info] Lossless Join (cont.)
> > > ![[Pasted image 20240930061823.png]]
> 
> > [!Info] Dependency Preserving Decomposition 
> > ![[Pasted image 20240930061902.png]]
> > 
> > > [!example]- Decomposition: Example
> > > ![[lec08-norm.pptx (dragged).pdf]]

> [!info] Boyce-Codd Normal Form (BCNF)
> ![[Pasted image 20240930062043.png]]
> 
> > [!info]- Decomposition into BCNF
> > ![[Pasted image 20240930062155.png]]
> > ![[Pasted image 20240930062205.png]]

> [!info] 3NF
> ![[Pasted image 20240930062106.png]]
> 
> > [!example]- Example
> > ![[Pasted image 20240930062121.png]]

> [!info]- Schema Refinement
> ![[Pasted image 20240930062233.png]]
> ![[Pasted image 20240930062243.png]]
> ![[Pasted image 20240930062251.png]]

> [!important] Normalization Summary
> - Bad schemas lead to redundancy
> 	- Redundant storage, update, insert, and delete anomaly
> - To "correct" abd schemas: decompose relations
> 	- Most be a lossless-join decomposition
> 	- Would like dependency preserving decompositions
> - Desired Normal Forms
> 	- BCNF: allow only super-key functional dependencies
> 	- 3NF: allow dependencies with prime attributes on the RHS
> 		- Allows a limited form of redundancy
> 		- Trades off performance (avoid joins) for redundancy