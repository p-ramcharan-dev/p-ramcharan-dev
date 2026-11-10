# Hi, I'm Ramcharan

I'm a freelance developer who makes slow Python code fast. I profile first, fix the algorithm where that is enough, move the hot loop to C++ only where it pays, and prove the result with benchmarks and tests that compare against the original.

## Featured work

**[fastrectpack](https://github.com/p-ramcharan-dev/fastrectpack)**: a drop-in C++17 accelerator for the open-source `rectpack` 2D packing library (about 387,000 downloads a month).

| Job | Before | After | Speedup |
|---|---|---|---|
| 5,000 rectangles, random sizes | 21.1 s | 0.14 s | 155x |
| 1,000 rectangles, random sizes | 3.5 s | 0.014 s | 246x |
| 2,000 sheet-cutting parts across 100 bins | 0.42 s | 0.078 s | 5x |

- **Identical output.** 472 tests compare every placement and the full internal state against the original, and all 14 benchmark cases match exactly.
- **Honest split.** Pure-Python algorithm fixes alone gave 1.7x to 7.5x. The C++ supplies the rest.
- **Honest limits.** Jobs spread over many bins gain about 5x, because that loop is still Python. Fractional sizes run at the original speed. The write-up says so.
- Checked under AddressSanitizer and UBSan, on Python 3.13 and 3.11.

[Case study](https://github.com/p-ramcharan-dev/fastrectpack/blob/main/CASE_STUDY.md) · [Benchmarks and method](https://github.com/p-ramcharan-dev/fastrectpack/blob/main/BENCHMARKS.md)

## How I work

1. **Measure.** Reproduce the slowness with a script anyone can run, then profile to see where the time really goes.
2. **Fix the algorithm first.** In the project above, about 90% of the time was one redundant clean-up step.
3. **Port the hot path to C++ only if it is still needed.** Same Python API, same results.
4. **Prove it.** Parity tests against the original, edge cases, property-based tests, memory-safety checks.
5. **Report honestly.** Real numbers, the spread, and what did not get faster.

## Tools

Python · C++17 · pybind11 · CMake · scikit-build-core · pytest · Hypothesis · AddressSanitizer / UBSan

## Contact

X: [@p_ramcharan_dev](https://x.com/p_ramcharan_dev)

Got a slow Python script or pipeline? Message me on X and I'll tell you where the time goes.
