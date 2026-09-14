# Skill: Boundary / Negative Testing

Use this skill when a feature has meaningful validation or limits.

## Negative coverage

Consider:
- Empty
- Whitespace
- Invalid format
- Invalid characters
- Malformed values
- Unexpected combinations
- Repeated actions
- Dependency failures

## Boundary coverage

When a limit is known, consider:
- min - 1
- min
- min + 1
- max - 1
- max
- max + 1

When a limit is unknown, do not invent a number. Express the behavior relative to the configured/approved limit.
