# Cerino for Claude

Most of what a company knows lives in a few people's heads. It's why a price
is what it is, how a job gets quoted, and who to call when a delivery slips.
Cerino turns that tribal knowledge into a company brain that your whole team
and Claude can rely on.

Every entry in the Brain is a decision, definition, process, policy,
commitment or fact that a named person approved. Connect Cerino and Claude
answers from that record. It tells you how your company actually does things,
links each source, names who signed off on it, and keeps what comes from the
Brain separate from general knowledge. Claude can also look up the people,
clients, projects and systems you work with, read your documents, and show
your goals, open issues and what is waiting for review.

When a conversation turns up something worth keeping, such as a decision, a
new client contact or a better way to run a process, Claude can propose it to
Cerino when you ask. Proposals wait in Cerino's Inbox until an owner or
manager approves them. This connection cannot approve anything itself, which
is what keeps the Brain worth trusting.

The Brain belongs to your company, not to any one assistant. The same
approved record works with other AI tools that support MCP, so your team can
change tools without starting over. Own what you know.

This plugin adds the Cerino connector and three skills that help Claude use it
well. One answers from what your team approved, with a link to each source. One
runs a short owner interview that builds the Brain. One gives a quick pass
through what is waiting for review.

## What you need

- A Cerino workspace and an invitation for your email address.
- A Google account with that email address. You sign in with Google the first
  time Claude connects to Cerino.
- Nothing else: there is nothing to install on your computer and no key to
  paste.

## Install

**Claude (web, desktop and mobile).** Once Cerino is listed in Claude's
directory, add the Cerino plugin from the directory, then open the plugin's
**Connectors** tab, connect Cerino and sign in with Google. On a Team or
Enterprise plan, an Owner adds the Cerino connector for the organization
first, and each member then connects with their own account.

Before the listing is live, add this repository as a plugin marketplace in
**Customize > Plugins > Add > Add marketplace**, using
`https://github.com/consciens/cerino-plugin`, and install Cerino from
it.

**Claude Code.** In a session:

```text
/plugin marketplace add consciens/cerino-plugin
/plugin install cerino@cerino
```

Or from your shell:

```bash
claude plugin marketplace add consciens/cerino-plugin
claude plugin install cerino@cerino
```

The first time a Cerino tool runs, Claude Code opens the Google sign-in in
your browser. Run `/mcp` to see whether Cerino is connected.

## Try it

- "How do we price a kitchen remodel?" Claude asks Cerino and answers from
  what your team approved, with a link to each source, kept apart from general
  advice.
- "We've decided to stop billing hourly from January. Propose that to
  Cerino." Claude drafts the proposal, asks you to confirm the wording, sends
  it, and gives you the link to review it in Cerino.
- "Interview me to set up our Cerino Brain." For a workspace owner: one
  question at a time, a few minutes at a time, each answer proposed with your
  go-ahead.
- "What's waiting for my review in Cerino?" Claude groups the waiting
  proposals so you can decide them in Cerino in a few minutes.

## What is in it

| Part | What it does |
| --- | --- |
| The Cerino connection (`.mcp.json`) | Connects Claude to `https://mcp.cerino.ai/mcp`, Cerino's server, signing in over OAuth. The tools come from that server. |
| `working-with-cerino` | When you ask about your own company's decisions, definitions, processes or numbers: ask the Brain, keep its answer apart from general knowledge, cite each source, and propose rather than assert. |
| `cerino-onboarding` | For a workspace owner who asks for it: a short interview about the business, one question at a time, each answer proposed to Cerino with the owner's go-ahead. |
| `whats-waiting-in-cerino` | What is waiting for review, grouped so a person can decide it in Cerino in a few minutes. |

## What it can and cannot do

- **It reads** your company's approved knowledge, the people, clients,
  projects and systems it records, its documents, goals, issues and ideas,
  and what is waiting for review, limited to what your own Cerino account may
  see.
- **It proposes.** A decision, a correction, a person or a goal is sent as a
  proposal that waits in Cerino's Inbox. Nothing enters the Brain until an
  owner or manager approves it there. Claude asks you before it proposes
  anything. A document you ask it to keep, an idea or an issue is saved in
  Cerino as what it is, and is never part of the Brain.
- **It cannot approve, reject or delete anything.** There is no tool for it.
  Approving happens in Cerino, by a person.

## What it sends and where

Everything goes to one place: Cerino's server at `mcp.cerino.ai`, run by
Logos Strategy Co. LLC, which does business as Cerino. It receives the inputs
of the tools Claude calls (your question, or the text of a proposal or
document you agreed to send) and the name of the assistant that sent it, and
not your conversation or Claude's own memory. The plugin
itself is text: its skills are instructions to Claude, and it runs no code on
your machine and contacts no other service.

- Privacy policy: <https://cerino.ai/privacy>
- Terms: <https://cerino.ai/terms>
- Connector documentation: <https://cerino.ai/docs/mcp>

## The rules live on the server

When Claude connects, Cerino's server sends the rules for treating the Brain
(cite each source, say "proposed" and never "saved", only approved knowledge
is part of the Brain). They reach every connected assistant whether or not
this plugin is installed. These skills say the same things in their own
words; where the two ever differ, the server's wording stands.

## Troubleshooting

- **Claude says Cerino is not connected.** Connect it from the plugin's
  **Connectors** tab in Claude, or run `/mcp` in Claude Code, and sign in with
  Google using the email address your invitation went to.
- **Sign-in does not reach your workspace.** Cerino is invite-only during
  early access: ask your workspace owner to invite the exact email address of
  the Google account you sign in with.
- **An answer is missing something you know was approved.** Ask again with
  narrower wording; each answer draws on the part of the Brain that matches
  the question.

## Support

<support@cerino.ai>. Security reports: <security@consciens.ai>.

## License

MIT. See [LICENSE](LICENSE).

## ChatGPT

The same repository is the ChatGPT plugin package, in the Agent Plugins
format: `plugin.json` (listing, review test cases and publication, under
`extensions.com.openai`), `mcp.json` (the same server), `skills/` and
`assets/`. Build the upload with:

```bash
zip -X -r cerino-chatgpt-plugin.zip plugin.json mcp.json skills assets LICENSE
```

`.claude-plugin/` and `.mcp.json` are Claude's and stay out of the ZIP.
Reviewer credentials and the demo video URL are entered in OpenAI's
dashboard, never in this repository.
