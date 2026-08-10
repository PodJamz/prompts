---
name: wayfinding
description: Plan a mission bigger than one session as a map of DECISION tickets, resolved one at a time until the route is clear - and bind worktrees to tickets so ambition does not become sprawl. USE WHEN work is too big for one session, when you do not know the route to the destination, when the fog is the problem rather than the code, or when worktrees and half-finished branches are piling up.
---

# Wayfinding

Plan enormous work by charting a map, not by writing a plan.

Adapted from `mattpocock/skills`. The original solves fog of war. This version also solves what fog leaves behind: dozens of worktrees, each begun as a good idea prompted ad hoc, none belonging to a stated destination. (The system this was extracted from measured 69 of them before adopting it.)

**Use it when you cannot see the route.** If the work fits one session and you already know the way, just do it; a map would be ceremony.

## The shape

You have a **start**, a **destination** you can describe but not reach, and fog between. The map clears the fog one decision at a time.

- **The map** is a single issue in your tracker labelled `wayfinder:map`. It is an INDEX, not a store: it gists each decision and links to it.
- **Tickets** are child issues of the map. Each is one decision, and each takes its own session.
- **The frontier** is the open, unblocked, unclaimed tickets: the edge of what can be decided right now.
- **Fog** is a `## Not yet specified` section on the map: real questions not yet sharp enough to be tickets.

Ticket when the question is already sharp, even if blocked. Fog when you cannot yet phrase it that sharply.

## Four ticket types

| Type | Who | What it is |
|---|---|---|
| **research** | an agent, away from keyboard | Read docs, APIs, the codebase. Surfaces facts a decision needs. Fire and forget. |
| **prototype** | with the human | A cheap rough artifact to react to. This is what stops a big map becoming waterfall. |
| **grilling** | with the human | Conversation. **The default case.** Interrogate until the decision is sharp. |
| **task** | either | Real-world work that must happen before a decision can be made. Unblocks without deciding. |

## Two modes

**CHART**: name the destination, grill breadth-first, create the map, create the tickets that can be specified now, wire the blocking relationships, fire the research tickets at agents, then STOP. Do not start resolving.

**WORK**: load the map, claim ONE ticket (assign it first), resolve it, post the resolution as a comment, close it, write the one-line gist back to the map, stop.

**Never resolve more than one ticket per session.** Research is the exception, because it runs unattended.

## Worktrees are bound to tickets

This is the anti-sprawl mechanism. A worktree declares the ticket it serves: created from it, named after it. A worktree with no ticket is not forbidden; it is simply visible as unbound.

| State | Meaning |
|---|---|
| bound, ticket open | live work |
| bound, ticket closed | done, safe to remove |
| unbound | an ad-hoc idea. Give it a ticket, or let it go. |

**Never auto-delete.** Some trees hold uncommitted work and that is unrecoverable. The mechanism is visibility; the deletion decision belongs to the human.

## Charting a map

1. **Name the destination.** What does done look like? If the human is unsure, that is the first grilling ticket.
2. **Grill breadth-first.** Do not go deep on the first interesting thing; you are mapping the SHAPE of the fog.
3. **Create the map issue** with the destination, the frontier, and a `## Not yet specified` section.
4. **Create only the tickets you can specify NOW.** Unphraseable questions go in the fog section.
5. **Wire blocking** with the tracker's native dependency relationship.
6. **Fire the research tickets** at agents immediately. They run while you talk. If you have a multi-agent board (see the boardroom skill), hand each research ticket to the agent whose discipline fits; the frontier can move overnight.
7. **Stop.** Charting is not resolving.

## Finishing

When the fog is gone, the map becomes a spec, and the spec becomes implementation tickets. The spec is non-persistent: once it is in the code, it can go. The decisions live in the closed tickets, where the primary source can be read rather than a summary.

## When NOT to use this

- Work that fits one session. Just do it.
- You already know the route. A map adds ceremony, not clarity.
- A bug. Fix it.

## The honest risk

Wayfinding is a discipline, and disciplines get abandoned when they cost more than the chaos. What decides it is whether agents can actually work the research tickets unattended. If a research ticket is still something the human has to do, the map is just another document.
