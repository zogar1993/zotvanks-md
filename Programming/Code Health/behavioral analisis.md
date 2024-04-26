## Description

Behavioral Analysis aims to know what are the legacy code bits that you need to focus your refactor on.

It is based on github history, and identifies hotspots based on:
 - various complexity metrics
 - change frequency

It can be done at a project level or at a file level.

The idea is that you don't need to refactor complex code that is not changed frequently.

## Off-boarding

When someone leaves the company, you can check how much of the codebase the person leaving was working on.

A good way to do knowledge transfer is to make them pair with someone who is staying, and refactor that code.

## Interesting Takes
- Code gets more and more features, or dies.
- Code gets more and more complex, unless taken care of.
- Ciclomatic complexity is the minimum amount of tests to cover a particular function.
- Legacy code is not only code that lacks quality, more importantly is code that you yourself haven't written.

## Sources
- [Prioritizing Technical Debt as If Time & Money Matters • Adam Tornhill • GOTO 2022](https://www.youtube.com/watch?v=w9YhmMPLQ4U) (Youtube)
- https://codescene.com/pricing (Paid Tool)