# sanity-action

Fail a build unless a repo's [Sanity](https://sanity.monster) readings are complete, current,
and taken by one model.

Readings are taken by developers, with `sanity check`, against the code they are about to
ship, and committed to `.sanity/`. This action never takes them: that would mean model
credentials in CI. It runs `sanity verify` over what was committed, which fails unless:

- **complete**: every function and file in scope has a reading;
- **current**: none is stale against the code as checked out, and none was taken under an
  older version of a question;
- **one instrument**: every reading names the same agent and model. This one is optional;
  see `consistent-reader`.

It needs no git history, no network beyond downloading Sanity, and no secrets.

## Usage

```yaml
jobs:
  readings:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v7
      - uses: monsterdept/sanity-action@v2
        with:
          version: 0.33.0
```

Runs on Linux, macOS and Windows runners, x86-64 or ARM64 (macOS: ARM64 only). It downloads
the headless `sanity` for the runner, about 16 MB, and caches it per version.

**v2 needs Sanity 0.33.0 or later**, the first release with headless builds. For an older
version, `monsterdept/sanity-action@v1` runs the Linux x86-64 AppImage.

| Input | Required | |
|---|---|---|
| `version` | yes | The Sanity release to verify with. |
| `path` | no | The repo to verify, relative to the workspace. Default `.` |
| `model` | no | Require this model rather than merely one model, e.g. `claude-sonnet-5`. |
| `harness` | no | Require this agent rather than merely one agent, e.g. `claude`. |
| `consistent-reader` | no | `false` passes readings taken by more than one agent or model. Default `true`. |

**Pin `version` to the release your team reads with.** A Sanity release that changes the
parser or a question can expire readings. The action's own tag (`@v2`) moves with fixes to
the action; the Sanity version moves only when you change it.

## License

MIT. Sanity itself is under the GPL, version 3 or later.

Locally, the same check is `sanity verify`.
