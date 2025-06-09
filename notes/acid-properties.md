# ACID Properties
ACID Properties ensure reliable transaction processing in relational databases
A database transaction should contain the following properties

## Atomicity
- All operations within a transaction are treated as a single unit - either all succeed or all fail.

- Follows "All or nothing" principle i.e. If any part of a transaction fails, the entire transaction is rolled back
- Database remains in a consistent state even if system failures occur


## Consistency
- Database must remain in a valid state before and after any transaction.

- All database rules, constraints, and triggers must be satisfied
- Data integrity is maintained across all tables
- Foreign key constraints, check constraints, and business rules are enforced

## Isolation
Concurrent transactions must not interfere with each other.

### Isolation Levels:

1. Read Uncommitted - Lowest isolation, allows dirty reads
2. Read Committed - Prevents dirty reads, allows non-repeatable reads
3. Repeatable Read - Prevents dirty and non-repeatable reads, allows phantom reads
4. Serializable - Highest isolation, prevents all concurrency issues


## Durability
Once a transaction is committed, changes are permanent and survive system failures.

- Committed data is stored in non-volatile storage
- Database can recover committed transactions after crashes
- Usually implemented through transaction logs and backup systems