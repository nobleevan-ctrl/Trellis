# Company brain build prompt

Fill in every `[bracket]`, then paste everything below the line into Claude while it has
access to your `claude-cowork/Trellis` folder. Leave a bracket blank if you don't know the
answer yet. Claude will list it as missing instead of guessing.

---

You are building the first version of the **Trellis company brain** inside my `claude-cowork/Trellis` folder.

A company brain is shared context that every AI agent and teammate works from: what the company believes now, what was decided and why, who owns what, how work gets done, and what we learned from past corrections. When one person corrects an agent, the fix goes into the brain so every future agent starts smarter. Keep it **small**: build only what the workflow below needs, and explain why each file exists.

## About Trellis

- **What Trellis is:** [one paragraph: the product or service, what problem it solves]
- **Who we serve:** [customer segments, and the pain points in their own words]
- **Offer and positioning:** [what we sell, pricing or packaging, our one-sentence positioning]
- **Approved claims:** [things we can say publicly, with sources. Write "none yet" if there aren't any]
- **Top priorities right now:**
  1. [priority]
  2. [priority]
  3. [priority]
- **Explicitly NOT a priority right now:** [things to ignore]
- **People and approval boundaries:** [name/role, what they own, what they can approve, e.g. "Me (founder): final call on positioning and pricing"]
- **Where the current truth lives (in priority order when sources conflict):**
  1. [e.g. this brain's accepted files]
  2. [e.g. project tracker]
  3. [e.g. CRM, contracts, Stripe]
- **Voice and style rules:** [how we write and talk, words to avoid]
- **Things agents must never do without asking:** [e.g. email customers, change prices, delete files, publish anything]

## The first workflow to build around

- **Workflow:** [one recurring task the team already does, e.g. writing content briefs, weekly report, sales follow-ups]
- **How often:** [e.g. weekly]
- **What a great result looks like:** [describe it, or point to a good past example file]
- **Corrections I keep repeating:** [the mistakes AI or people keep making on this task]

## Your job

**Step 0: Look before you build.** List what's already in `claude-cowork/Trellis`. Read whatever is relevant (docs, notes, past examples) and use it as source material. Don't overwrite or delete existing files. If something you'd create already exists, tell me and propose a merge.

**Step 1: Create this structure** (create a file only if this workflow needs it; leave anything I can't maintain empty):

```
CLAUDE.md                  ← instructions for Claude: read brain/map.md first, open only the files needed, follow the correction loop
AGENTS.md                  ← same instructions, for Codex / Cursor / other agents
brain/
  map.md                   ← the front door, max one screen (template below)
  company-brief.md         ← what we do, who we serve, offer, positioning, approved claims
  priorities.md            ← what matters now and what doesn't, with a "last reviewed" date
  learnings.md             ← table: date | what went wrong | root cause | routed to | status (proposed/accepted/rejected) | reviewer
  decisions/               ← one file per decision (YYYY-MM-DD-name.md): owner, status, what it supersedes, why
  people/                  ← owners and approval boundaries
  projects/                ← current work and status; finished work goes to projects/archive/
  policies/                ← rules that apply every time (voice, claims, safety), plus correction-routing.md
  skills/                  ← proven ways to do a task: when to use it, steps, good example, common mistakes
  workers/                 ← repeatable jobs an agent can run end to end
```

**Step 2: Write `brain/map.md`** using this shape, filled in from my answers:

```
# Trellis company map
## What we do        (one short paragraph)
## What matters now  (3 priorities)
## Source order      (highest wins when sources conflict)
## Navigation        (one line per file/folder: what it contains)
## Rules
- Use the newest accepted information.
- When two sources conflict, follow the source order.
- If the answer is missing, say what you could not find.
- Never turn a guess into company knowledge.
```

**Step 3: Identify the minimum knowledge** this workflow needs: facts, decisions, policies, preferences, and approval boundaries. Put each in the right file.

**Step 4: Write the first policy** in `brain/policies/` for the most important rule behind this workflow (use my repeated corrections).

**Step 5: Write the first worker** in `brain/workers/[workflow-name].md` with: trigger, inputs (including which brain files it reads), numbered steps, exact output format and destination, when to stop and ask a human, and the reviewer.

**Step 6: Write `brain/policies/correction-routing.md`** with this table and loop:

| The correction is a… | Route it to |
|---|---|
| Missing or outdated fact | company-brief.md or projects/ |
| New strategic choice | new file in decisions/ |
| Repeated preference | policies/ |
| Proven technique | skills/ |
| Repeatable sequence | workers/ |
| Dangerous action | a mechanical gate (permission rule, hook, check), not just a note |

Loop: work → correction → find root cause → route → **human review** → share → better future work.
Rule: agents only ever add learnings as `proposed`. Only a human from `people/` marks them `accepted`.

**Step 7: Create a `/learn` command** (if this environment supports custom slash commands or skills). Given a correction, it finds the root cause, routes the fix with the table, makes the minimal edit, logs a `proposed` row in `learnings.md`, and shows me the diff and who should review it.

## Return to me

1. The file tree you created, with one line on why each file exists
2. The source hierarchy
3. The first policy
4. The first worker spec
5. The correction and review loop
6. **Every piece of information you're missing from me**, as a checklist
7. **The exact first test to run:** a real instance of the workflow I can do right now, and what to watch for

Keep the first version small. Don't try to capture the whole company. Every hesitation, guess, or stale answer in the first test tells us what the brain needs next.
