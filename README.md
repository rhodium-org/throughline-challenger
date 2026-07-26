# throughline-challenger

A planned tool in the **throughline** family that interrogates the *semantic*
links between requirement items and surfaces those that need a human to confirm
or reject them.

## Why

`tl check` validates a requirements graph's **structure** — that every non-root
item reaches a root through a well-formed grounding edge, forming an acyclic
root-terminating DAG. It cannot, from the edge alone, judge whether the graph is
**semantically** sound:

- **Modal-strength drift** — does a parent actually entail its child, and at the
  stated modal strength? A child that says MUST/every/always where its parent (or
  a `satisfies`-linked external standard) grants only MAY/can/able-to passes the
  gate silently. The mismatch runs both directions — a node can over-claim
  relative to its descendants *and* relative to a standard it adopts by reference.
- **Prose-mention-without-edge** — an item's free text can cite another item by
  UID (e.g. `SR-0004` naming `NG-0004`) while its `links` block records no such
  edge. `tl check` inspects only the grounding edge, never the prose, so the
  dangling cross-reference is invisible to it.

Human ratification is the only current guard against these, and it is fallible.
throughline-challenger automates the challenge pass — it never rewrites the graph
itself; it flags items for a human to confirm, rescope, or reject.

## Status

Design stage. The requirements graph lives under `idd/` (bare `tl`, no composed
sources yet). Run `tl -C idd context` for the agent brief and `tl -C idd check`
to validate. No implementation yet.
