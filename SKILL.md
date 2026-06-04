---
name: steal-the-code
description: Legacy name for Find OSS Alternative. This skill is no longer the maintained entry point. Use lumpinif/find-oss-alternative@find-oss-alternative for current OSS alternative discovery, repo verification, license review, and Use / Borrow / Avoid / Build New recommendations.
---

# Steal the Code Legacy

This skill is legacy and may no longer receive active updates.

Use the maintained skill instead:

```bash
npx skills add lumpinif/find-oss-alternative
```

Use without installing:

```bash
npx skills use lumpinif/find-oss-alternative@find-oss-alternative
```

Canonical repository:

https://github.com/lumpinif/find-oss-alternative

## When This Legacy Skill Is Invoked

1. Tell the user that the maintained skill is `find-oss-alternative`.
2. Give the install/use command above.
3. If the user still wants to continue in the current session, use the current
   Find OSS Alternative workflow:
   - find open-source alternatives and public precedents;
   - verify GitHub repo, license, maintenance, and code evidence;
   - rank by practical fit, not stars alone;
   - return `Use / Borrow / Avoid / Build New`;
   - credit builders and respect licenses.

