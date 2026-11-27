# Security policy

## Reporting a vulnerability

Please report a vulnerability privately, never in a public issue, pull request or discussion:

1. Open the repository's **Security** tab and choose **Report a vulnerability**
   ([new private report](https://github.com/teamrig/teamrig-relay/security/advisories/new)).
2. Say what an attacker can do, the teamrig-relay version, the operating system or host it runs on, and the steps
   that show it. A proof of concept helps; keep it to what shows the flaw.

The report is seen only by the maintainer and you. Until the fixed version is out, the fix's branch, commits, pull
request and tests describe the hardening, not the flaw. We answer in the report, work on the fix there, and publish the
advisory with the fixed version once it is out, crediting you unless you ask not to be named.

## What counts

The relay forwards sealed bytes between one user's own machines and is built to see no content (design in
[teamrig/teamrig#2449](https://github.com/teamrig/teamrig/issues/2449)), so the flaws that matter most are those that
break that promise or let something cross a line it should not:

- the relay, or anyone who runs or watches it, can read, change, replay or forge what it forwards;
- a machine that is not the user's own can join, send to or receive from that user's machines;
- a secret, key or private path written where it should not be: a log, a commit, an issue or a release;
- a dependency or GitHub Action with a known advisory that the relay's code reaches.

A finding that needs the attacker to already run commands as the same user on one of that user's machines is out of
scope: that user can do anything the relay can.

## Supported versions

The relay has no release yet. Once it has, only the newest released version gets fixes.
