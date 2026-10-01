# Security Policy

This policy covers every repository under
[giorgioparri](https://github.com/giorgioparri): the Home Assistant custom
integrations, the Lovelace cards, and the Home Assistant Apps.

## What is in scope

The code in these repositories: the integrations, the cards, and the packaging
of the Apps — Dockerfiles, service scripts and configuration.

The software those Apps package is **not** in scope, nor is Home Assistant
itself. A flaw in BamBuddy, Bambu Studio or InfluxDB belongs upstream, and each
App's `DOCS.md` links to the right project. If you are not sure which side a
problem falls on, report it here anyway and I will forward it.

## Reporting a vulnerability

Do not open a public issue, and do not describe the problem in a pull request.

Go to the repository's **Security** tab and use **Report a vulnerability**.
That opens a private thread visible only to you and me, and it stays private
until a fix is published.

Useful things to include: which repository and version, what an attacker can
achieve, and the steps to reproduce it. A proof of concept helps but is not
required — a clear description of the flaw is enough to get started.

## What happens next

I maintain these projects in my spare time, so I cannot promise a fixed
response time. In practice you can expect a first reply within a few days. I
will tell you whether the report is accepted, and once a fix is released I will
credit you in the changelog unless you would rather stay anonymous.

Please give me a reasonable window to publish a fix before disclosing the issue
elsewhere. These projects run inside people's homes, on systems that control
heating, solar inverters and EV chargers, and their users update on their own
schedule.

## Supported versions

Only the latest release of each project gets fixes. There are no maintenance
branches: a security fix ships as a new release, which HACS or the Home
Assistant Supervisor then offers as a normal update.