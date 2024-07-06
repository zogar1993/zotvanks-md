# Sagas
- A way to efficiently deal with distributed systems without incurring in feral concurrency and death star architectures.
- A Failure Control mechanism
- Kind of like event Sourcing applied to coordinating services

## Requests
- Can abort
- Idempotent

## Compensating Request
- Semantic undo
- Cannot abort
- Idempotent
- Commutative

## Characteristics
- Sagas move forward until all complete or all revert
- there is no atomicity
- there is no isolation

## SEC
- SEC (saga excecution coordinator), can be many and highly available
- start and end sagas
- Distributed saga log (fault tolerant and highly available)
- If something fails and some other parallel task did not yet succeed, wait for it to succeed in order to roll it back.

### Saga log structure
name:
request:
compensating request:
status: (mutable)

## Sources

- https://www.youtube.com/watch?v=1H6tounpnG8
- https://gotocon.com/chicago-2015/presentation/Applying%20the%20Saga%20Pattern
- https://gotocon.com/dl/goto-chicago-2015/slides/CaitieMcCaffrey_ApplyingTheSagaPattern.pdf