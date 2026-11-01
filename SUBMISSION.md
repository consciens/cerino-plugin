# Submitting the Cerino plugin to Claude's directory

How to submit this repository as a **plugin bundle** in Anthropic's directory,
paired with the **Cerino** MCP connector (`https://mcp.cerino.ai/mcp`), and how
to keep it current once it is listed. Written 2026-11-01 for Stephen.

**Sources, read first-hand on 2026-11-01:**
[Publish to the directory](https://claude.com/docs/directory/publish),
[Submit your plugin](https://claude.com/docs/plugins/submit),
[Plugin pre-submission checklist](https://claude.com/docs/plugins/pre-submission-checklist),
[Plugin structure and testing](https://claude.com/docs/plugins/build),
[Plugin manifest reference](https://code.claude.com/docs/en/plugins/manifest-reference),
[Install and manage plugins (Claude Code)](https://code.claude.com/docs/en/discover-plugins)
and the
[Software Directory Policy](https://support.claude.com/en/articles/13145358-anthropic-software-directory-policy).
Anything marked **(not first-hand)** is inferred or was not on those pages;
check it in the portal.

## 1. Order and ownership

1. **The connector goes first.** Submit `https://mcp.cerino.ai/mcp` as an
   **MCP connector** (`control` → `docs/operations/connector-directory-submission.md`, §5).
2. **Then this plugin**, from **the same claude.ai organization** (Consciens).
   Anthropic: "when the connector and a plugin bundle that references it are
   submitted from the same organization, you can pair the two listings." The
   plugin's `.mcp.json` already points at the same URL, so someone with both
   sees one set of tools.
3. **Whoever submits first owns the listing.** "The first organization to
   submit a given repository folder holds that listing, and the portal refuses
   a second organization's submission of the same one." Submit from the
   Consciens organization, as an Owner (or a member given the **Directory**
   permission on Enterprise).

Where in the portal the pairing is made is **not on the pages above (not
first-hand)**: look for it on the plugin's or the connector's page after both
are submitted, and ask `directory@anthropic.com` if it is not there.

## 2. Pre-submit checklist

Do these in order. Each is a yes or no.

- [ ] `main` holds the version to submit (the directory follows `main`).
- [ ] The repository is public, as the directory needs before a listing goes
      live (claude.com/docs/plugins/submit). It started on 2026-11-01 from one
      clean commit, with no earlier history; the working history is in the
      private, archived `consciens/cerino-claude-plugin`.
- [ ] The Claude GitHub App is installed on this repository.
- [ ] `claude plugin validate .` at the repository root prints
      `Validation passed` with nothing to report (it did on 2026-11-01, Claude Code 2.1.316).
- [ ] **The icon is right.** `.claude-plugin/icon.png` is the connector's
      mark: the bold three rings in brand blue on a transparent ground,
      rendered at 1024px from `https://mcp.cerino.ai/icon.svg` (`platform` →
      `apps/runtime/src/server/mcp/brand-icon.ts`), so the plugin and the
      connector show the same icon. The validator says it "may become the
      listing icon only once: the first time the plugin is saved or submitted
      in the developer portal. Adding or changing it later does not change the
      icon." If Trayton's final small-size files land first, re-render from
      them **before** the first save.
- [ ] **The name is right.** `name` is `cerino`, the plugin's permanent
      identity; `displayName` is `Cerino`; `author.name` is `Cerino`.
- [ ] The connector is submitted (ideally listed) from the Consciens
      organization.
- [ ] Your GitHub account is connected on claude.ai **in the Consciens
      organization** and can push to `consciens/cerino-plugin` (the
      portal checks this before it lets you create or submit).
- [ ] `https://cerino.ai/privacy`, `/terms` and `/docs/mcp` are live and
      signed off (connector runbook DIR2), and none of them mentions Microsoft
      sign-in.
- [ ] `support@cerino.ai` and `security@consciens.ai` are monitored (a test
      message to each is answered).
- [ ] **Tested on each surface:**
  - claude.ai: zip the repository folder, **Customize > Plugins > Add >
    Upload plugin**, connect Cerino from the plugin's **Connectors** tab,
    and run the four prompts under "Try it" in the README;
  - Claude Code: `claude --plugin-dir .` from the repository, `/mcp` to sign
    in, the same four prompts.
  Each answer cites with named links, says "proposed" and never "saved", asks
  before proposing, and shows no ids or slugs.
- [ ] Every tool name the skills mention is on the live server (see §5).

## 3. The form, step by step

Portal: <https://claude.ai/directory/manage> → **Submit new** →
**What would you like to submit?** → **Plugin bundle**.

### Source

| Field | Our value |
| --- | --- |
| **Repository** | `consciens/cerino-plugin` |
| **Plugin path (optional)** | leave empty (the plugin is at the repository root) |
| **Branch or tag (optional)** | leave empty to follow the default branch, `main` |

Select **Validate**. Fix anything marked **Blocking**, push, and select
**Re-validate**. A **Policy hold** can be submitted; a reviewer reads it.

### Listing details

Read from `plugin.json` and the README, **not typed into the form**. To
change one, edit the file, push and validate again. What it will show:

| Shown as | Source | Value |
| --- | --- | --- |
| Name | `displayName` | Cerino |
| Publisher | `author.name` | Cerino |
| Short description | `description` | Cerino is your company brain, the human-approved source of truth for how your business operates. This plugin connects Claude to it and adds three skills. Claude answers from what your team approved and links each source, a short owner interview builds the Brain, and a quick pass shows what is waiting for review. Claude proposes, and a person approves in Cerino. |
| Description | `README.md` | the README (it opens with the listing one-liner) |
| Icon | `icon` | `.claude-plugin/icon.png` |
| Documentation | `documentationUrl` | https://cerino.ai/docs/mcp |
| Privacy policy | `privacyPolicyUrl` | https://cerino.ai/privacy |
| Terms | `termsOfServiceUrl` | https://cerino.ai/terms |
| Website | `author.url` / `homepage` | https://cerino.ai, https://cerino.ai/docs/mcp |
| Licence | `license` and `LICENSE` | MIT |

**Category.** The plugin pages above name no category field for a plugin
bundle **(not first-hand)**. If the portal asks, choose **Productivity**.
`keywords` includes `productivity`, and the Claude Code marketplace entry
sets `"category": "productivity"`. There is no `supportUrl`: Cerino has no
support web page, and the field takes an `https://` URL, not an address; the
README gives `support@cerino.ai`.

### Data handling

| Question (as the docs paraphrase it) | Our answer |
| --- | --- |
| Does the plugin read or store personal data? | It **reads** personal data only through its declared connector, Cerino: the signed-in person's identity and the company records their account may see (names, roles and contact details of people the company works with). The plugin itself stores nothing; it is text. |
| Does it send data to services other than its declared connectors? | **No.** Its only destination is `https://mcp.cerino.ai/mcp`. |
| How long does it keep data? | The plugin keeps nothing. Cerino keeps what the organization adds until the organization deletes it or closes its account; source material up to 365 days; operational logs up to 90 days; approval audit records for the life of the account (https://cerino.ai/privacy). |
| Is it intended for people under 18? | **No.** Cerino is a business product, not directed to anyone under 16 (privacy policy), and the plugin is for workspace members at work. |

The exact wording and answer choices are in the portal, not the docs
**(not first-hand)**; answer the first question in the portal's terms, and
choose "yes, through the declared connector" if it offers that.

### Compliance

- **Contact email:** `support@cerino.ai` (Anthropic writes here about the
  submission). Use your own address if you would rather receive it first.
- Select all four acknowledgements (the docs do not list them; read each).

### Review and submit

- **How new versions reach the directory:** keep **GitHub push webhook**
  (default). After submitting, select **Set up push updates**; it needs admin
  access to the repository on GitHub.
- **Auto-publish passing versions:** leave **off** for the first submission,
  so each version is published by a deliberate press until the listing has
  settled. Anthropic decides the publish setting on review in any case.
- Select **Submit for review**.

### After submitting

The directory scans the newest commit on `main` (validation again plus a
security scan), a person reviews a new listing, and a version that passes is
live only after **Publish** on the plugin's page. Status is on the plugin's
page under **Submissions**; the **Versions** tab lists each scanned commit.

## 4. Text for the directory in the connector's voice

These are the words the listing shows, already in the files. Keep the two
listings saying the same thing.

- **One-liner (connector and plugin):** Cerino is your company brain, the
  human-approved source of truth for how your business operates.
- **What the plugin adds, in one sentence:** the skills that teach Claude to
  use Cerino well: answer from what your team approved and cite it, ask
  before proposing, check for duplicates first, and send people to the review
  link, never claiming anything was saved.
- **Words to avoid in listing copy:** "memory" and "memories" for the Brain's
  contents (they collide with Claude's Memory feature); say "the Brain",
  "approved knowledge", "proposals". Never "Microsoft" (sign-in is Google
  only). Never "Consciens" as the brand (the legal line names Logos Strategy
  Co. LLC, doing business as Cerino).

## 5. Keeping it current after it is listed

**Release.** Merge to `main` and raise `version` in
`.claude-plugin/plugin.json` in the same pull request (1.0.0 → 1.0.1 for
wording, 1.1.0 for a new skill). The directory picks the commit up by the
webhook or on its schedule (select **Check for new commits** to hurry it),
scans it, and publishes it according to the plugin's publish setting. The
listing keeps serving the last published version until a new one is
published, including when a new one fails or is held. The name and short
description follow the live version; the **icon does not change** after the
first save.

**Claude Code users who installed from this repository's marketplace**
(`cerino@cerino`): third-party marketplaces do not auto-update by default.
They get a new version with `/plugin marketplace update cerino` or
`claude plugin update cerino@cerino`, and only when `version` was raised,
because a set `version` pins them to it.

**When the server's tools change.** The skills name tools by name. Before
merging a platform change that renames, removes or adds a tool, check the
skills the same day:

```bash
grep -ohE '`[a-z_]+`' skills/*/SKILL.md | tr -d '`' | sort -u
```

Every name it prints, except the parameter `entity_ids`, must be one of the
26 tools on the remote server (`platform` →
`apps/runtime/src/server/mcp/`; on 2026-11-01: `add_document`, `add_idea`,
`comment_on_proposal`, `fetch`, `find_entities`, `get_brain_context`,
`get_brain_status`, `get_document`, `get_entity`, `get_metric_definition`,
`get_process_map`, `list_goals`, `list_ideas`, `list_issues`,
`list_metric_definitions`, `list_pending_additions`,
`list_pending_suggestions`, `list_proposal_comments`, `open_issue`,
`propose_change`, `propose_entity`, `propose_goal`, `propose_memory`,
`search`, `search_documents`, `trace`). `approve_suggestion`,
`reject_suggestion`, `approve_addition` and `reject_addition` exist only on
the local transport and must never appear in a skill.

**Tell Anthropic about material changes.** The policy requires notice of
material changes to functionality (3.H). A new kind of write, a new data
destination or a change in who can approve is material; reword the README's
"What it sends and where" in the same pull request.

**Delist.** On the plugin's page, the header menu → **Delist plugin**.
People who installed it stop getting updates and their copy may be removed.
