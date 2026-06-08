# Contribution #1: feat: Respect RateLimit headers in default REST backoff implementation

**Contribution Number:** 1  
**Student:** Rabiul Hossain  
**Issue:** https://github.com/meltano/sdk/issues/2012  
**Status:** Phase I — Complete

---

## Why I Chose This Issue

I chose this issue because it sits at the intersection of API engineering and reliability — two areas I'm actively building skills in. The Meltano SDK is a widely-used Python framework for building Singer taps and targets, and rate limiting is a real-world problem that every developer hitting external REST APIs eventually encounters. Right now, the SDK's default backoff implementation ignores `RateLimit` and `Retry-After` headers that APIs send back, meaning it falls back to a generic exponential backoff instead of respecting what the server is actually telling it to do. That's both inefficient and potentially disrespectful to API providers' stated limits.

This issue is a strong fit for my skills because I'm comfortable with Python, familiar with REST API patterns, and have worked with HTTP headers and request/response cycles before. I'm also motivated by the learning opportunity: the SDK's backoff logic touches `requests-cache`, `backoff`, and HTTP response handling in ways I'll have to understand deeply before I can change them safely. The issue is labeled "Accepting Pull Requests," has active maintainer engagement, and has a clear definition of what "done" looks like — the SDK should parse `RateLimit-Reset`, `RateLimit-Remaining`, and `Retry-After` headers and use those values to drive backoff timing instead of ignoring them.

---

## Understanding the Issue

### Problem Description

The Meltano SDK's default REST stream implementation uses a generic exponential backoff strategy when it receives rate-limit responses (typically HTTP 429) from APIs. It does not read the `RateLimit-Reset`, `RateLimit-Remaining`, or `Retry-After` headers that many APIs include in their responses — headers that tell the client exactly how long to wait before retrying. As a result, the SDK may wait too long or too short, and may make unnecessary additional requests that further violate the API's rate limits.

### Expected Behavior

When the SDK receives a rate-limit response from a REST API that includes `RateLimit-Reset`, `RateLimit-Remaining`, or `Retry-After` headers, it should parse those headers and use the indicated wait time to drive its retry/backoff behavior — rather than defaulting to a fixed or exponential backoff interval.

### Current Behavior

The SDK's backoff logic ignores rate limit headers entirely. Every rate-limited response is handled with the same generic backoff strategy regardless of what the API is communicating in its response headers.

### Affected Components

- The default REST backoff/retry logic in the Meltano SDK (likely in `singer_sdk/streams/rest.py` or a related backoff utility module)
- HTTP response handling in the base REST stream class
- Potentially the `backoff` library integration and how wait functions are configured

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

- [Meltano SDK Docs](https://sdk.meltano.com)
- [GitHub Issue #2012](https://github.com/meltano/sdk/issues/2012)
- [requests HTTP library docs](https://docs.python-requests.org)
- [backoff library docs](https://github.com/litl/backoff)
