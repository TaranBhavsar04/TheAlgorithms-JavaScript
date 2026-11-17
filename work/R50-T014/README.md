# R50-T014 evidence

- Source contract location: `Sorts/SimplifiedWiggleSort.js:1-5`
- Focused test: `Sorts/test/SimplifiedWiggleSort.test.js`
- Literal fixtures and independently established expectations: [3,1,2], [2,2,1], [1,2,3], [3,2,1], [7], plus 100 seeded arrays
- Review note: Invariant is the actual documented wiggle order (<=, >= alternating) plus multiset preservation; the function is not an ascending sorter. A deterministic duplicate-heavy fixture exposed a non-terminating QuickSelect path. The implementation now sorts a copy and interleaves the lower and upper halves, preserving the documented weak wiggle invariant without mutating the input.
- Focused command: `python3 work/R50-T014/check.py`
- Native repository command after `npm ci`: `npm test -- --run` is represented by the focused Vitest invocation; run the complete suite with `npm test`.

The runner prints the actual Python and Node versions and propagates a non-zero test exit.

## Verification record

- Direct Node.js invariant run: PASS (10 fixed cases and 100 deterministic bounded numeric arrays); checked wiggle order, multiset preservation, and no input mutation.
- `python3 work/R50-T014/check.py`: BLOCKED because Vitest is not installed and the npm registry is unreachable in this environment (`ENOTCACHED`).
- `npm test`: BLOCKED (`vitest: not found`) for the same missing dependency.
- Runtime used: Python 3.13.5; Node.js v22.16.0.
