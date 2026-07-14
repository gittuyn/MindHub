# MindHub RFC Foundation Design

- Date: 2026-07-14
- Decision owner: gittuyn
- Status: Approved for specification

## Purpose

Establish MindHub's RFC governance and define the boundary of RFC-0001 before designing the Knowledge Model, lifecycle, protocol, database, API, or implementation.

## Governance Model

MindHub uses the following RFC states:

```text
Draft → Review → Accepted / Rejected → Superseded
```

The RFC author drafts the proposal and responds to review. The project owner, gittuyn, is the sole final decision-maker. This is the initial governance model and may be changed later only through an RFC.

- Draft RFCs may change freely.
- Moving to Review requires a review deadline.
- Material changes during Review must be recorded in revision history.
- Accepted confirms a design decision; it does not claim implementation.
- Rejected RFCs remain in the repository with their rejection rationale.
- Accepted RFCs are not rewritten to introduce major semantic changes. A new RFC supersedes them.
- Dependencies between RFCs must be explicit.

Voting, champions, appeals, and periodic mandatory review are outside the initial process.

## Initial RFC Structure

```text
rfcs/
├── README.md
├── 0000-rfc-process.md
├── template.md
└── 0001-mindhub-manifesto.md
```

- `README.md` indexes RFCs and their current states.
- RFC-0000 defines the governance process and begins as Accepted based on the owner's approval of this design.
- `template.md` supplies the required structure for future RFCs.
- RFC-0001 begins as Draft and is reviewed section by section.

## RFC Template

Every RFC includes:

- Summary
- Motivation
- Goals and Non-Goals
- Terminology
- Detailed Design
- Alternatives Considered
- Security, Privacy, and Governance
- Compatibility
- Risks and Open Questions
- Decision
- Revision History

Metadata identifies the RFC number, title, author, status, creation date, review deadline when applicable, decision owner, and dependencies.

## RFC-0001 Scope

RFC-0001 answers:

- Why MindHub is needed.
- What MindHub is and whom it serves.
- What "Knowledge Operating System" means.
- Which principles constrain later designs.
- How MindHub differs from Agent Memory, RAG, vector databases, note-taking systems, and MCP.
- Which responsibilities are explicit non-goals.
- How to judge whether later work remains aligned with the manifesto.

RFC-0001 does not define:

- Knowledge entities, identity, relations, or version semantics; RFC-0002 owns these.
- Lifecycle states and transitions; RFC-0003 owns these.
- OpenMemory interfaces and transport semantics; RFC-0004 owns these.
- Database, API, framework, deployment, or user-interface choices.
- Cognitive metaphors as normative engineering evidence.

DIKW and hippocampus/neocortex analogies may explain inspiration, but they do not establish correctness.

## Product Position

MindHub is an open, shared knowledge hub in which AI Agents participate first and humans retain ultimate control. It captures, governs, evolves, and exchanges long-lived knowledge with provenance, scope, and history.

AI Agents normally perform ingestion, organization, linking, deduplication, conflict detection, and low-risk governance. Humans do not review every knowledge item, but retain authority over policy, permissions, high-impact changes, rollback, and deletion.

Automation must be configurable and revocable. It is constrained by scope and risk. Agent actions that alter knowledge state or meaning must be traceable. Human control does not imply approval of every operation; routine work is automatic and exceptional risk is escalated.

The physical-versus-logical deletion semantics remain deliberately assigned to RFC-0003.

## Manifesto Success Criteria

RFC-0001 succeeds when:

- A proposed capability can be classified as inside or outside MindHub's responsibility.
- Knowledge changes can be traced to sources, actors, and history.
- Multiple Agents can share knowledge without bypassing access scope or governance policy.
- Routine governance can be automated while high-risk or irreversible changes can be escalated to humans.
- Storage, model, and transport implementations can change without redefining core knowledge semantics.
- Humans can pause automated governance, revoke authority, correct outcomes, and exercise final deletion authority.

## Validation

Before acceptance or publication, the initial RFC set must satisfy all of the following:

- No unexplained placeholders such as `TBD` or `TODO`.
- RFC-0001 does not define subjects owned by RFC-0002, RFC-0003, or RFC-0004.
- Normative requirements are testable or reviewable rather than aspirational only.
- `Conception.md` remains unchanged as the source concept document.
- Index states, dependencies, links, and revision histories agree.
- Git history records the introduction and later decisions.

## Delivery Sequence

1. Commit this approved design specification.
2. Create RFC-0000, the template, the index, and RFC-0001 Draft.
3. Review RFC-0001 with the decision owner.
4. Accept RFC-0001 only after explicit owner approval.
5. Begin RFC-0002 before database, API, or application implementation.

