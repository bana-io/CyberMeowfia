Some information:

1. The device I am using is the Samsung S26 Ultra (SM-S948B).
2. Kernel version is `6.12.69-android16-6-p8021103-abogkiS948BXXU3ZZF7-4k`.
3. I wrote a detailed report in `./SM-S948B/BUG-REPORT.md` and also at <https://news.ycombinator.com/item?id=48834309 and <https://github.com/NebuSec/CyberMeowfia/issues/46>..

## Constraints

1. You do not push any code.
2. You start a Docker container for each command you execute so I can reproduce things when I run them.
3. You cannot break anything after each step, that is, everything should remain buildable.
4. Create a branch and make commits to this branch only.

## Success Criteria

1. You port the exploit/POC to my device which is the `SM-S948B`, and produce a binary named `poc`. Consult `IonStack/CVE-2026-43499/exploit/Makefile` for how to go about building it.
2. Code should compile without errors within a Docker container.
3. Some brief sanity tests that I can run, again, within a Docker container before deploying.
