# Correction routing

When work gets corrected, fix the layer that caused the mistake, not just the output.

| The correction is a…        | Route it to                          |
|-----------------------------|--------------------------------------|
| Missing or outdated fact    | `company-brief.md` or `projects/`    |
| New strategic choice        | new file in `decisions/`             |
| Repeated preference         | `policies/`                          |
| Proven technique            | `skills/`                            |
| Repeatable sequence         | `workers/`                           |
| Dangerous action            | mechanical gate (hook, CI check, permission rule), not just a note |

## Loop
work → correction → route → **human review** → share (merge to main) → better future work

## Review rule
Nothing becomes shared knowledge until a human with authority over that area (see `people/`)
approves it. In practice, every brain change goes through a pull request.
