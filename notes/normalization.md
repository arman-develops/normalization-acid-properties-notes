# Database Normalization

## Definition
A technique used to organize data in relational databases.
It accomplishes two things:
- Eliminate data redundancies
- Ensure integrity of data
- Minimizes update anomalies
- Improves query perfomance

Basically invplves breaking down larrge complex conceptual tables into smaller tables while maintaining data relationships.

## Types of Normalization

### First Normal Form (1NF)
At this level, each column should contain only atomic values i.e. 
- Each column is indivisible.
- Atomicity in this case means only one piece of data should exist in a cell of a column
- Each column should have unique names
- Each column should contain data of a single type

### Second Normal Form (2NF)
- Records  must be in 1NF
- Non key attributes depend only on the primary key i.e. There should be a direct relationship between each column and the primary key.
- Eliminates partial dependencies

### Third Normal Form (3NF)
- Must be in 2NF
- Non-key attributes should not depend on other non key attributes
- Every non-key attribute must depend directly on the primary key

### Boyce-Codd Normal Form (BCNF)
- Must be in 3NF
- Stricter version of 3NF that handles certain edge cases

### Fourth Normal Form (4NF)
- This is a normalization level that builds on BCNF by dealing with multi-valued dependencies.

### Fifth Normal Form (5NF)
- 5NF is the highest normalization level that addresses join dependencies. It is used in specific scenarios to further minimize redundancy by breaking a table into smaller tables.

# Example Scenario
We will use a sample of a library database to build on the normalization concepts

