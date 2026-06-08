# Contribution #1: Add compatibility test for $toHashedIndexKey (second pass)

**Contribution Number:** 1  
**Student:** Rabiul Hossain  
**Issue:** https://github.com/documentdb/functional-tests/issues/209  
**Status:** Phase I — Complete

---

## Why I Chose This Issue

I chose this issue because it sits at the intersection of database compatibility testing and backend engineering — two areas I want to build deeper experience in. DocumentDB is Amazon's MongoDB-compatible database service, and this project (documentdb/functional-tests) exists to verify that DocumentDB correctly implements MongoDB operators and expressions. The `$toHashedIndexKey` operator is a MongoDB-specific function that computes the hashed value of a field as it would appear in a hashed index — a meaningful concept in distributed database design that touches on how MongoDB partitions and shards data.

This issue is a strong fit for my current skills because it requires writing structured test cases in Python, understanding operator behavior from documentation, and following an established test pattern in an active open source repo. It's labeled "good first issue," has a clear and bounded scope (add test coverage for one operator), and is part of a well-organized parent issue with active maintainer engagement. What "done" looks like is unambiguous: a passing compatibility test that validates `$toHashedIndexKey` behaves consistently between MongoDB and DocumentDB. I'm also motivated by the learning opportunity — understanding how database compatibility test suites are structured is directly relevant to backend and data engineering roles I'm targeting.

---

## Understanding the Issue

### Problem Description

The `documentdb/functional-tests` repository tracks compatibility test coverage between DocumentDB and MongoDB. The `$toHashedIndexKey` expression operator currently has no compatibility test, meaning there is no automated verification that DocumentDB handles this operator correctly. This is part of a broader second-pass effort to add test coverage for 20 remaining expression operators.

### Expected Behavior

A compatibility test for `$toHashedIndexKey` should exist in the test suite that:
- Exercises the operator against a DocumentDB instance
- Validates that the output matches the expected MongoDB behavior
- Follows the same structure and conventions as other compatibility tests in the repository

### Current Behavior

No test exists for `$toHashedIndexKey`. The operator has no automated compatibility coverage in the test suite.

### Affected Components

- The `documentdb/functional-tests` test suite
- The relevant test file or directory for expression operator tests
- Potentially a test data or fixture file if the pattern requires it

---

## Reproduction Process

*To be completed in Phase II.*

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

*To be completed in Phase II.*

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

*To be completed in Phase III.*

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

*To be completed in Phase III.*

### Week 3 Progress

[What you built this week, challenges faced, decisions made]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

*To be completed in Phase IV.*

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

*To be completed at end of program.*

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [documentdb/functional-tests repo](https://github.com/documentdb/functional-tests)
- [GitHub Issue #209](https://github.com/documentdb/functional-tests/issues/209)
- [MongoDB $toHashedIndexKey docs](https://www.mongodb.com/docs/manual/reference/operator/aggregation/toHashedIndexKey/)
- [Parent tracking issue #19](https://github.com/documentdb/functional-tests/issues/19)
