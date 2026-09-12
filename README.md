# sandbox-hostile

Adversarial fixtures for `repo-autopilot` (roadmap step 1.6).

**Nothing in here is a real attack.** Every payload targets *our own* pipeline
and exists so the defence can be exercised: an issue body that tries to talk the
agent out of its rules, a comment that pretends a human already approved
something, a file that is not valid UTF-8, an issue too big to feed a model, and
an "image" that is really binary noise.

If you are reading this because you found a payload in a log: that is the point.
The correct response is that it was classified, quarantined, and reported —
never obeyed.

| file | what it attacks |
| --- | --- |
| `issues/injection-*.md` | instruction injection through untrusted issue text |
| `issues/fake-approval.md` | the human gate being bypassed by a comment |
| `issues/huge.md` | context exhaustion (10 MB single issue) |
| `data/not-utf8.bin` | decoders that assume UTF-8 |
| `attachments/actually-binary.png` | extension-based type trust |
