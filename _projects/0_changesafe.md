---
layout: page
title: "ChangeSafe: An AI Infrastructure Change Airlock"
description: A v0.1 safety boundary that converts AI-generated infrastructure recommendations into typed, schema-validated, transactionally applied patches with deterministic policy checks and hash-bound decision receipts.
importance: 1
category: engineering
---

**Independent project, 2026.**

ChangeSafe asks a narrow question: before an AI-generated infrastructure change is
applied, how do you _prove_ it is safe to apply?

The v0.1 answer is an airlock. AI-generated recommendations are converted into typed
declarative patches, validated against strict schemas and permitted state paths, and
applied transactionally against a cloned infrastructure model — never directly against
production.

On top of that boundary sit deterministic policy checks for management reachability,
protected resources, blast radius, rollback completeness, and required verification.
Fail-closed domain states are enforced, inverse rollback is tested, and every decision
emits a hash-bound receipt so the outcome is auditable after the fact.

Production execution remains intentionally disabled in v0.1 — the point of this version
is the safety boundary itself, not the automation it would eventually gate.
