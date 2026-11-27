# Contributing

teamrig-relay is part of [teamrig](https://github.com/teamrig/teamrig) and works the way teamrig does: its
[CONTRIBUTING.md](https://github.com/teamrig/teamrig/blob/main/CONTRIBUTING.md) and
[how to report and contribute](https://github.com/teamrig/teamrig/blob/main/docs/issues-and-pull-requests.md),
the rules for AI tools included, apply here too. This page holds what is the relay's own. The design is
[teamrig/teamrig#2449](https://github.com/teamrig/teamrig/issues/2449); there is no relay code yet, so the build and
test steps join this page with the first code.

## How we work

- **An issue per change**: open one with a form here first (bug, feature, task or design), so the change and its reason
  are agreed before it is built. A design issue is talk only until the maintainer marks it agreed.
- **One branch per change**, cut from the newest `origin/main`, landed through a pull request and the merge queue;
  no one pushes to `main`.
- **One logical change per commit**: a fix with its tests, a refactor apart from what it enables, a mechanical change
  alone. A commit past 400 changed non-test lines or 15 non-test files carries a `Large-commit: <reason>` line saying
  why it cannot be split; CI's commit size rule fails one without it.
- **Conventional subjects**: `<type>(<area>): <what>`, the area optional; the types are `feat`, `fix`, `perf`,
  `refactor`, `docs`, `test`, `build`, `ci`, `chore` and `revert`, with `!` before the colon for a breaking change.
  CI's commit subject gate fails any other, since the release raises the version from `main`'s subjects.
- **Tests with the change**: a new behaviour gets a test that fails without it, a bug fix a regression test that fails
  on the old code.
- **Typed code with no casts**: no `any`, no `as unknown as`; narrow `unknown` with a type guard.
- **Docs in the same pull request** as the change they describe.

## Sign-off (DCO)

Every commit must carry a `Signed-off-by:` line that matches the commit author, certifying the
[Developer Certificate of Origin 1.1](https://developercertificate.org/). Add it with:

```sh
git commit -s
```

CI's DCO gate fails a pull request with a commit that lacks it.

## Pull requests

- **The description**: the template asks for What, Why, Reach, Changes, Risks, Old-code proof, Tests and Issue
  (`Fixes #<n>` or `Refs #<n>`), then the checklist.
- **From a fork**: fork the repository, branch off its `main`, and open the pull request against this repository's
  `main`. CI runs it with no secrets and a read-only token, and an outside contributor's run waits for the maintainer
  to approve it.
- **Your commit e-mail**: the `Signed-off-by:` line carries your commit e-mail, and the scrub refuses an e-mail address
  in a commit message unless it is one of GitHub's no-reply addresses. Before your first commit, set the no-reply
  address GitHub shows under Settings, Emails: `git config user.email <id>+<user>@users.noreply.github.com`.
- **Checks**: CI runs teamrig's own gates on the relay (the scrub of the tree and the commits, the DCO sign-off, the
  commit size rule and the commit subject gate, from a pinned teamrig commit) and a dependency review; the one check
  `main` requires, `every check passed`, passes only when every one of them did.
- **Review**: a code owner (`.github/CODEOWNERS`: the maintainer) reviews the code and approves the last push; a new
  push dismisses an approval given before it. A change to `.github/` also gets a security review.

## Licence

The relay is under the [Apache License 2.0](LICENSE): a contribution you submit is under it too (its section 5). The
name follows [TRADEMARKS.md](TRADEMARKS.md).
