---
name: whats-waiting-in-cerino
description: Use when the user asks what is waiting for review or approval in Cerino, what needs their decision, whether anything is stuck, or for a review of pending proposals. Lists and groups the waiting proposals and points to where each is decided in Cerino; it cannot approve anything.
---

# What is waiting in Cerino

Help a person get through their Cerino Inbox quickly. You prepare; they
decide, in Cerino.

1. Use `list_pending_suggestions` for proposals waiting on a person, and
   `get_brain_status` when the user asks how much is waiting overall or
   whether anything is stuck. For an owner or manager,
   `list_pending_additions` shows links and details held back from an
   approved proposal because its reviewer could not see them.
2. If Cerino shows a card listing the items with their buttons, do not
   repeat them as a list or table; say in a sentence or two what matters most
   and what to do next. Otherwise, group what came back so it can be decided
   in batches: by area, named by its title, then by kind (decisions,
   definitions, processes, facts). Within a group, put anything that
   contradicts approved knowledge first and say so.
3. For each item give one line in plain words: what it says, who proposed
   it, and how long it has waited. Never show ids or slugs.
4. Say what you notice that helps a decision, briefly: a duplicate, a
   proposal that conflicts with another, one that is vague. If the user wants
   to add a note for the person deciding, draft it, and post it with
   `comment_on_proposal` once they confirm the wording (it is recorded as
   theirs, and a reply decides nothing). `list_proposal_comments` shows the
   existing thread.
5. End with where to decide: the review links the results carry, as markdown
   links, and one line that approving happens in the Cerino app, by an owner
   or a manager with Decide access to that area. There is no tool here to
   approve or reject; if asked, say so and give the link.

Never describe a waiting proposal as part of the Brain. It counts once a
person approves it.
