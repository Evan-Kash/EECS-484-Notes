> [!info] Formal Query Languages
> - Two types
> 	- Declarative: <span style="color:rgb(0, 112, 192)">Relational Calculus</span> 
> 		- Describe what a user wants, rather than how to compute it
> 	- Procedural: <span style="color:rgb(0, 112, 192)">Relational Algebra</span> 
> 		- Operational, very useful for representing execution plans
> - Query Languages <span style="color:rgb(0, 112, 192)">!=</span> programming languages
> 	- QLs not expected to be "Turing complete"
> 	- QLs not intended to be used for complex calculations
> 	- QLs support easy, efficient access to large data sets
> 
> ![[Pasted image 20240914213058.png]]

> [!info] Relational Algebra
> 
> > [!info]- Relational Algebra
> > - Input: relational instances
> > - Output: relational instances
> > - Specified using the schemas
> > 	- May produce different results for different instances
> > 	- But schema of the result is fixed
> 
> > [!info]- Numeric Algebra
> > - Input: Rational Numbers
> > - Output: Rational Numbers
> > - Operators: $+, -, \times, \frac{\cdot}{\cdot}$
> 
> > [!question]- Question
> > - The smallest set of numbers that is CLOSED with respect to the operators $\{+, -, \times \}$ is:
> > 	A. Natural Numbers
> > 	<u>B. Integers</u>
> > 	C. Rational Numbers
> > 	D. Real. Numbers
> 
> > [!info] Relational Operators
> > - <span style="color:rgb(0, 112, 192)">**Selection**</span> $\sigma$: Selects a subset of rows from relation
> > - <span style="color:rgb(0, 112, 192)">**Projection**</span> $\pi$: Deletes unwanted columns from relation
> > - <span style="color:rgb(0, 112, 192)">**Cross-product**</span> $\times$: Allows us to combine two relations
> > - <span style="color:rgb(0, 112, 192)">**Set-difference**</span> $-$: Tuples in relation 1, but not in relation 2
> > - <span style="color:rgb(0, 112, 192)">**Union**</span> $\cup$: Tuples in relation 1 and relation 2
> > - Additional operations (constructed from basic ops - not essential but very useful)
> > 	- Intersection, **Join**, Division, Renaming
> > - Because algebra is closed, we can **compose** operators
> > 
> > > [!info]- Selection
> > > ![[Pasted image 20240914214137.png]]
> > 
> > > [!info]- Projection
> > > ![[Pasted image 20240914214158.png]]
> > 
> > > [!info]- Set Operations: Union ($\cup$), Intersection ($\cap$), Set-Difference ($-$)
> > > ![[Pasted image 20240914214316.png]]
> > 
> > > [!info]- Cross-Product (Cartesian Product) ($\times$)
> > > ![[Pasted image 20240914214428.png]]
> > 
> > > [!info]- Rename Operator
> > > $\rho_{\text{AFTER}}\text{(BEFORE)} \text{ or } \rho(\text{AFTER, BEFORE})$
> > > <br>
> > > - Use cases:
> > > 	- Shorthand
> > > 	- Self-joins
> > > 	- If two relations have the same field
> > > 
> > > ![[Pasted image 20240914214748.png]]
> > 
> > > [!info]- Derived Operators: Joins
> > > - Most common way of combining information from two tables
> > > - **Conditional join or $\Theta$-join**
> > > 	- ![[Pasted image 20240914215131.png]]
> > > - **Equijoin**
> > > 	- Join conditions consists only of equalities
> > > - **Natural Join**
> > > 	- Like equijoin but drops the duplicate columns 
> > > 	- ![[Pasted image 20240914215145.png]]
> > > - Despite equivalence, joins faster than cross-product
> 
> > [!example]- Example
> > ![[lec05-RA (dragged).pdf]]
> 
> > [!info]- Derived Operators: Division
> > - Useful for queries like:
> > 	- "Find all the sailrs who have reserved **<span style="color:rgb(0, 112, 192)">all</span> boats**"
> > 	  
> > ![[Pasted image 20240914215419.png]]
> > 
> > > [!example] Example
> > > ![[lec05-RA (dragged) 2.pdf]]