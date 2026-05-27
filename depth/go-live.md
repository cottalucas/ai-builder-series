# Go-Live

> Pre-production checklist. Run before every prod deploy.

## Code

- [ ] All tests pass
- [ ] No `TODO` or `FIXME` in changed files
- [ ] No console logs or debug code
- [ ] Secrets in env vars, not in code

## Data

- [ ] Migrations tested on staging
- [ ] Rollback path verified
- [ ] Backups confirmed recent

## Ops

- [ ] Error monitoring active
- [ ] Alerts configured
- [ ] On-call has context

## User

- [ ] Breaking changes communicated
- [ ] Onboarding flow tested fresh
- [ ] Support / docs updated
