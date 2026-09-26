# root — sanity assessment

2 of 2 read · 0 unpredicted

Each entry below is one **reading**, of a function or of a whole file. An
agent was given its name, signature, neighboring names and comments — never
its body — and wrote down what it expected to find. Then it opened the file.
The gap between the two is the finding. A file's own entry is titled `the file
itself` and asks whether the header at the top describes what is actually in
there.

`read at` is a hash of the body as it was when the reading was made. When it
stops matching the code, the reading is marked STALE and goes back in the
queue.

What this is and how to add to it: [README.md](README.md)

## calc.py

### the file itself
- spec 3 · read at `952dc5e666cd` · commit `fad460d` · read by claude-sonnet-5 · asked for sonnet · via claude · when 2026-09-26T04:47:39Z · by ross@rossturk.com · cold reading · reading 1 of its run
- expected: A tiny module with a single function add(a, b) that returns a + b. No header docs.
- found: Single function add(a, b) returning a + b.
- predicted: full · documented: none · derivable: yes · legible: not judged · trap: no

### `add`
- spec 3 · read at `99e90f6044d3` · commit `fad460d` · read by claude-sonnet-5 · asked for sonnet · via claude · when 2026-09-26T04:47:38Z · by ross@rossturk.com · cold reading · reading 1 of its run
- expected: Returns a + b. Simple two-line function, no side effects.
- found: Returns a + b.
- predicted: full · documented: none · derivable: yes · legible: full · trap: no · test: no
