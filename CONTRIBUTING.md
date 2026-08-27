# Contributing

Thanks for taking the time. These notes apply to every repository under
[naked-head](https://github.com/naked-head); anything repository-specific is in
that repository's own README.

## Before you write code

**Open an issue first** for anything that changes behaviour — a bug report, or
a feature request describing what you want to do. It costs you five minutes and
can save you an afternoon: the change may already be planned, conflict with
something in flight, or be out of scope. Use the issue forms, they ask for what
is actually needed to reproduce a problem.

Typo fixes, documentation corrections and translation updates need no issue.
Send the pull request.

## Pull requests

- One branch per concern, named `<type>/<short-description>` with type in
  `feat`, `fix`, `ci`, `docs`, `chore`.
- Commit messages in English, [Conventional Commits](https://www.conventionalcommits.org)
  style: `fix: stop the card flickering on state change`.
- Code, comments, documentation and commit messages in English. User-facing
  translations are the exception, obviously.
- CI has to be green. It runs the same checks you can run locally — see below.
- Describe what the change does and, if it fixes an issue, link it.

## Licensing of contributions

By opening a pull request you agree that your contribution is licensed under
the same licence as the repository you are contributing to, as stated in its
`LICENSE` file. Your copyright stays yours: this only makes the terms explicit,
so the project can keep distributing your work under the licence users already
rely on.

## Running the checks locally

Which of these applies depends on the repository you are in.

### Custom integrations (`custom_components/`)

Python 3.13.

```bash
pip install ruff
ruff check .
python tests/test_<name>.py   # one file per test module
```

Home Assistant's `hassfest` and the HACS validation also run in CI; both check
metadata rather than behaviour, so they rarely fail on a code change.

### Lovelace cards (`src/`, `dist/`)

Node 20.

```bash
npm ci
npm run build
npm test
```

`dist/` is committed on purpose, so manual installs keep working. **Rebuild and
commit it together with your change** — CI fails if the committed bundle does
not match what `src/` produces. To add or update a translation, edit the files
under `src/translations/` and rebuild; the strings are bundled into `dist/`, not
fetched at runtime.

### Home Assistant Apps (`homeassistant-addons`)

Docker with buildx.

```bash
docker build -t <app>:test <app>/
docker build -t supervisor-mock test/mock/
./<app>/test/smoke.sh
```

Shell scripts are checked with `shellcheck`, `config.yaml` with `yamllint`.
Note that these Apps package software published by others: a change to the
packaging belongs here, a change to the packaged software belongs upstream. The
links are in each App's `DOCS.md`.

## Reporting a security issue

Do not open a public issue. Go to the repository's **Security** tab and use
**Report a vulnerability**: it opens a private thread visible only to you and
me, and it stays private until a fix is published. Please give me a reasonable
window to fix the problem before disclosing it elsewhere.