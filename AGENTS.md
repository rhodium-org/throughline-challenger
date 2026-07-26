# Working in this repo

This project is managed by **throughline** (Intent-Driven Development). Its
requirements graph lives under `idd/`.

- Run **`tl -C idd context`** first — it is the authoritative, config-generated
  agent brief for this graph.
- Change the graph **only through the `tl` CLI** — never hand-edit an item's
  structure, links, status, or UID. (Rich prose in `text`/`rationale` and
  attributes is edited in the YAML; structure is not.)
- Keep **`tl -C idd check`** green before you commit.
- AI/hybrid-origin items are provisional — propose them; a human ratifies with
  `tl -C idd ratify <UID> --by <who>`. Do not self-ratify.
- Every commit should cite the IDD node(s) it supports.
