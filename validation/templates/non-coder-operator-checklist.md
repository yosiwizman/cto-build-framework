# Non-Coder Operator Checklist

A practical cheat sheet for running a governed build session without a technical background.
Keep this open during every session.

---

## Before You Start

- [ ] Read the handoff document from the last session (if there is one)
- [ ] Check that git status is clean — the AI tool should report no uncommitted changes
- [ ] Kill any old server or preview windows from previous sessions before starting new ones
- [ ] Know what you are building today — write the goal in one sentence before you open the AI tool

---

## Choose the Right Tool

| Task | Use This |
|------|----------|
| Planning what to build | Chat (Claude.ai or similar) |
| Actually building it | Claude Code or agentic coding tool |
| Reviewing what was built | Claude Code with read-only scout pass first |
| Reviewing evidence | Your own eyes — do not delegate final verification to AI |

The AI tool does not choose the right tool for you. You do.

---

## During the Build

- [ ] One slice at a time — if the AI is doing more than one thing at once, stop it and scope it back down
- [ ] After each slice: check that it works before continuing
- [ ] Save a checkpoint (commit) after every slice that works — do not wait until the end
- [ ] If something breaks: roll back to the last checkpoint, do not patch on top of broken work
- [ ] If the AI is making changes you didn't ask for: stop the session, re-scope, restart

---

## How to Verify (Without Knowing Code)

You don't need to read the code to verify results. You need to:

1. **Open the software** and use it yourself
2. **Test each requirement** from your original list, one by one
3. **Check it on the device you actually use** (phone, tablet, desktop — wherever it matters)
4. **Screenshot or record** anything you verified — this is your evidence
5. If it doesn't work as expected: it is not Proven. Do not accept "it should work" — verify it yourself

---

## What to Collect Before Claiming Success

Before calling a project done, confirm you have:

- [ ] Every requirement tested by you personally (not just reported as working by the AI)
- [ ] Screenshots or recordings of each verified requirement
- [ ] A release gate completed (see `governance/release-gates.md`)
- [ ] A passing gate verdict recorded
- [ ] An evidence packet filed (see `validation/templates/evidence-packet-template.md`)

If any of these are missing, the project is not done — it is in progress.

---

## When to Stop and Ask for Clarification

Stop and get a second opinion when:

- The AI is making changes you don't understand and can't verify
- The scope has grown beyond what you originally planned
- Something broke and a quick rollback didn't fix it
- The AI is recommending a "quick workaround" instead of a real fix
- You're not sure whether what you're seeing is the old version or the new version

It is always cheaper to pause and ask than to continue into an unverified state.

---

## Proof vs. Model Summary

The AI can produce a summary that says "everything is working." That summary is not proof.

Proof is:
- You opened the software
- You tested the feature yourself
- It worked as required
- You captured evidence (screenshot, recording, or written log)

A confident-sounding AI summary with no founder verification is not an evidence packet. Do not file it as one.

---

## Session End Checklist

- [ ] Verify all slices from this session are working
- [ ] Save a clean checkpoint (commit with a specific message — not "update")
- [ ] Write a handoff note: what was done, what's next, any open questions
- [ ] Close stale servers and preview windows

---

_This checklist is part of the CTO Build Framework. It reflects the operating discipline in `governance/llm-operating-discipline.md`, translated for a non-technical operator._
