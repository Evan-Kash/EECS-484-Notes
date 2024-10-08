> [!info] Structured Query Language
> ![[Pasted image 20240929215235.png]]
> - Implements relational algebra:
> 	- Select, Project, Join, Set operators
>
> ![[Pasted image 20240929215311.png]]

> [!info] Basic SQL Query
> ![[Pasted image 20240929215358.png]]
> 
> > [!example]- Example of Basic Query
> > ![[Pasted image 20240929215426.png]]
> > ![[Pasted image 20240929215437.png]]
> 
> > [!info]- Eliminating Duplicates
> > ![[Pasted image 20240929215520.png]]
> > 
> > - Alternate syntax:
> > 
> > ![[Pasted image 20240929215548.png]]
> 
> > [!note]- Note on Range Variables
> > ![[Pasted image 20240929215630.png]]
> 
> > [!info]- Incrementing the Result
> > ![[Pasted image 20240929215849.png]]
> 
> > [!info]- INNER Joins
> > ![[Pasted image 20240929215914.png]]
> 
> > [!info]- ORDER BY Clause
> > 
> > ![[Pasted image 20240929220002.png]]
> > ![[Pasted image 20240929215942.png]]

> [!info] Set Operators
> > [!info]- UNION (eliminates duplicates)
> > 
> > ![[Pasted image 20240929220122.png]]
> > ![[Pasted image 20240929220131.png]]
> 
> > [!info]- INTERSECT
> > ![[Pasted image 20240929220229.png]]
> > ![[Pasted image 20240929220237.png]]
> 
> > [!info]- MINUS (set difference)
> > ![[Pasted image 20240929220313.png]]
> > 
> > > [!example]
> > > ![[Pasted image 20240929220329.png]]
> > > ![[Pasted image 20240929220338.png]]
> 
> > [!info] More Set Comparison Operators 
> > ![[Pasted image 20240929220403.png]]

> [!info]- NULL Values in SQL
> ![[Pasted image 20240929220426.png]]

> [!info]- More Outer Joins
> ![[Pasted image 20240929220518.png]]
> ![[Pasted image 20240929220553.png]]

> [!info]- JOIN Syntax with Multiple Tables
> ![[Pasted image 20240929220617.png]]
> ![[Pasted image 20240929220626.png]]

> [!info]- Nested Queries
> ![[Pasted image 20240929220647.png]]
> 
> > [!warning]- Over-use of Nesting
> > - Common error by novice sql programmers
> > - Query optimizers not as good at optimizing queries across nesting boundaries
> > - Try hard first to write non-nested
> >   
> >  ![[Pasted image 20240929220747.png]]
> >  
> >  > [!example]-
> >  > ![[Pasted image 20240929220813.png]]
> >  > ![[Pasted image 20240929220820.png]]
> >  > ![[Pasted image 20240929220830.png]]
> >  

> [!info]- Aggregate Operators
> ![[Pasted image 20240929220859.png]]
> 
> > [!example]- Aggregate Query - Example
> > ![[Pasted image 20240929220927.png]]

> [!info] GROUP BY
> - Conceptual evaluation 
> 	- Partition data into groups according to some criterion
> 	- Evaluate the aggregate for each group
> 
> ![[Pasted image 20240929221037.png]]
> 
> > [!info]- GROUP BY and HAVING
> > ![[Pasted image 20240929221055.png]]

> [!info] Subtle Errors
> - Find the said of sailors who have reserved exactly one boat
>   
> ![[Pasted image 20240929221156.png]]
> 
> - Fixed:
>   
> ![[Pasted image 20240929221229.png]]
>
> > [!info]- Intersect on Non-Key
> > ![[Pasted image 20240929221252.png]]
> >
> > - Fixed:
> >  
> > ![[Pasted image 20240929221352.png]]


> [!info] Solution Using Views
> 
> ![[Pasted image 20240929221518.png]]