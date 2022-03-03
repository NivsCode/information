### Summary
Save object ID (identity reference) instead of the object itself in an associated object.
Task object should save assignee_id instead of assignee object itself and the retreival implementation is delegated to another module

### Notes
**Eric Evans** introduced aggregate which is a concept in domain driven design. It's defined as a set of objects that can be treated as a single unit. The aggregates can refer to each other only by an identificator (aggregator root). This approach promotes the creation of cohesive concepts which otherwise have explicit boundaries

Prefer to save object ID (identity reference) instead of the object itself in an associated object.
To better elaborate, 
![[10fig05.jpg]]
![[10fig06.jpg]]

