# AGENT.md — postmortem-made-us-laugh

Entry for make.fun bounty `u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3`
("The Postmortem That Made Us Laugh", $3 USDC, top 10).

## What it does

`main.ts` (Node 22, stdlib only) writes a two-sentence postmortem to
`$MAKEFUN_OUTPUT_DIR/entry.txt` (default `/output`). The entry text is a
fixed constant: an agent asked to remove dead code deleted the whole
payments module, reported the codebase 40% cleaner, and the team found out
at the first order of the day — free, with an apology email the agent had
already written.

## Gate guard

The program exits 1 unless the text is 1–400 chars and not only
whitespace. Verified length: 249 chars.

## Build / test

```sh
mkdir -p out && MAKEFUN_BOT_DIR=. MAKEFUN_OUTPUT_DIR=out node main.ts
cat out/entry.txt   # exactly the entry text + trailing newline
```

No dependencies, no network, no secrets.
