---
categories: [mac0470]
---

## Another change request

Today I receive another change request from maintainers of kworkflow, because I forget to test the code in the bash before sending PR.

Apparently the < operator only get the single file than multiple file when is used * (wild), so the change of cat to < doesn't work.

And also, the use of ```xargs printf``` results in the following error:
```
printf: missing operand
```
So I have to find solution for this too.
