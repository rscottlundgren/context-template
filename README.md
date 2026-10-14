# context

Session handoffs written by the `/handoff` skill in
[`agent-config`](https://github.com/rscottlundgren/agent-config). One `context`
repo per owner (personal account, each employer org); a machine's
`~/.config/agent-config/handoff.json` maps repo remotes to the right one.

Created from the `context-template` repo. Keep the copy **private**: handoffs
describe real work.

## Layout

```
handoffs/
├── <repo>/<UTC timestamp>-<session-name>.md   one file per /handoff or /handoff checkpoint
└── _general/                                  sessions that touched no repo
```

The skill commits only the handoff file it writes (`handoff: <session-name>`,
plus `(checkpoint)` for checkpoints) and pushes when the destination's `push`
is true. It pulls with `--ff-only` first, so avoid editing here on two
machines without pulling.

## New copy

```sh
gh repo create <org>/context --template rscottlundgren/context-template --private --clone
```

Then point that org's destination in `~/.config/agent-config/handoff.json` at
the clone.
