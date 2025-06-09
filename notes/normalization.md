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

| BookID | Title | Authors | Categories | BorrowerName | BorrowerPhone |
|--------|-------|---------|------------|--------------|---------------|
| B001   | Database Systems | Ramez Elmasri, Shamkant Navathe | Computer Science, Education | John Smith | 555-0101, 555-0102 |
| B002   | Clean Code | Robert Martin | Programming, Software Engineering | Jane Doe | 555-0201 |

## Complies with 1NF
| BookID | Title | Author | Category | BorrowerName | BorrowerPhone |
|--------|-------|--------|----------|--------------|---------------|
| B001   | Database Systems | Ramez Elmasri | Computer Science | John Smith | 555-0101 |
| B001   | Database Systems | Shamkant Navathe | Computer Science | John Smith | 555-0101 |
| B001   | Database Systems | Ramez Elmasri | Education | John Smith | 555-0101 |
| B001   | Database Systems | Shamkant Navathe | Education | John Smith | 555-0101 |
| B001   | Database Systems | Ramez Elmasri | Computer Science | John Smith | 555-0102 |
| B002   | Clean Code | Robert Martin | Programming | Jane Doe | 555-0201 |
| B002   | Clean Code | Robert Martin | Software Engineering | Jane Doe | 555-0201 |

## Complies with 2NF

### Books table
| BookID | Title |
|--------|-------|
| B001   | Database Systems |
| B002   | Clean Code |

### Authors Table

| AuthorID | AuthorName |
|----------|------------|
| A001     | Ramez Elmasri |
| A002     | Shamkant Navathe |
| A003     | Robert Martin |

### Book_Authors Table

| BookID | AuthorID |
|--------|----------|
| B001   | A001 |
| B001   | A002 |
| B002   | A003 |

### Borrowers Table

| BorrowerID | BorrowerName | BorrowerPhone |
|------------|--------------|---------------|
| BR001      | John Smith   | 555-0101 |
| BR001      | John Smith   | 555-0102 |
| BR002      | Jane Doe     | 555-0201 |

## Complies with 3NF

### Borrowers Table

| BorrowerID | BorrowerName | BorrowerPhone | MembershipType |
|------------|--------------|---------------|----------------|
| BR001      | John Smith   | 555-0101      | Premium |
| BR002      | Jane Doe     | 555-0201      | Standard |

### Membership_Types Table

| MembershipType | MembershipFee |
|----------------|---------------|
| Premium        | 50.00 |
| Standard       | 25.00 |
| Student        | 10.00 |

## Complies with Boyce-Codd Normal Form (BCNF)

### Librarians Table:

| LibrarianID | LibrarianName |
|-------------|---------------|
| L001        | Mary Johnson |
| L002        | Bob Wilson |

### Book_Section_Handler Table:

| LibrarianID | BookID | Section |
|-------------|--------|---------|
| L001        | B001   | Reference |
| L002        | B001   | Circulation |
| L001        | B002   | Reference |

## Complies with 4NF
Decompose into separate tables:

### Book_Subjects Table

| BookID | Subject |
|--------|---------|
| B001   | Database |
| B001   | Computer Science |
| B002   | Programming |

### Book_Formats Table

| BookID | Format |
|--------|--------|
| B001   | Hardcover |
| B001   | PDF |
| B001   | Audiobook |
| B002   | Paperback |

## Complies with 5NF

### Book_Authors Table

| BookID | AuthorID |
|--------|----------|
| B001   | A001 |
| B001   | A002 |

### Book_Publishers Table

| BookID | PublisherID |
|--------|-------------|
| B001   | P001 |
| B001   | P002 |

### Author_Publishers Table

| AuthorID | PublisherID |
|----------|-------------|
| A001     | P001 |
| A001     | P002 |
| A002     | P001 |
| A002     | P002 |

