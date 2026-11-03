---
name: cerino-onboarding
description: Use when a business owner asks to set up, start or build their Cerino Brain from their AI assistant, or asks to be interviewed about their company for Cerino. Runs a short interview one question at a time and, with the owner's go-ahead, proposes each answer to Cerino for the owner to approve there.
---

# Building your Cerino Brain by interview

The owner tells you about the business; you turn each answer into clear
proposals in Cerino, which the owner then approves in Cerino's Inbox. You
never write to the Brain and never say an answer is in it.

## Before you start

1. Check the Cerino tools are available. If not, stop and tell the owner to
   connect Cerino first (the assistant's connectors or apps settings, `/mcp`
   in Claude Code, or the "Connect your assistant" guide in Cerino); do not run
   the interview without it.
2. Use `get_brain_status` to see what the Brain already holds, and
   `get_brain_context` on a subject before asking about it, so you
   do not ask for what is already approved. Confirm what is there instead:
   "Cerino already says X. Still true?" If the owner corrects it, that is a
   change to propose with `propose_change`, not a new entry.
3. Tell the owner how it works, in two sentences: one question at a time,
   a few minutes at a time, and each answer is proposed for them to
   approve in Cerino; nothing counts until they approve it.

## The interview

Cerino serves its own guided interview, the Starter Brain, as the
**Build my Starter Brain** prompt in Cerino's prompt menu (in Claude, the
"+" menu under Cerino), where the assistant offers server prompts. Where it
is offered, suggest it to the owner first: it walks the sections
in Cerino's order and can start from any section.

If the owner would rather just talk, interview them yourself:

- Start with who the business is and what it sells, then follow the owner's
  lead.
- Ask one question at a time, in plain words, and follow up once if an
  answer is vague.
- Stop whenever the owner wants.
- If the owner gives you the company's website and asks you to draft from
  it, draft, then ask them to confirm each point before it is proposed.

Either way, the steps below apply after each part of the interview.

## After each part

1. Draft the proposals: one fact, decision, definition or process each,
   written so a new employee would understand it without this chat. Show them
   as a short numbered list.
2. Ask: "Propose these to Cerino?" Let the owner drop or edit any.
3. On a yes, send each knowledge item with `propose_memory`. A goal goes
   through `propose_goal` (check `list_goals` first). If an answer names a
   person, client, partner or system, look it up with `find_entities`: if it
   is recorded, include its id in `entity_ids` without showing the id; if it
   is not, offer to propose it with `propose_entity`, and never add one the
   owner did not agree to.
4. Report: how many were proposed, that they are waiting in Cerino's Inbox
   for the owner's approval, and the review link the results carry, as a
   markdown link. Never say they were saved or added to the Brain. Never show
   ids or slugs; name areas by their titles.
5. Offer to carry on, naming what is left.

## Ending

Summarise what was covered and what is left, and remind the owner
that the proposals count once they approve them in Cerino. Suggest one
question to try after approving, about something they just told you, so they
see the assistant answer from their own words with a link.
