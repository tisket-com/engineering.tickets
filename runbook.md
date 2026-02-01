# Engineering Runbook

## On-Call Procedures

### Incident Response
1. Acknowledge the alert
2. Assess severity and impact
3. Communicate status in #engineering-incidents
4. Investigate and resolve
5. Write post-mortem if P1/P2

### Escalation Path
- L1: On-call engineer
- L2: Team lead
- L3: Engineering manager

## Common Issues

### Database Connection Errors
Check connection pool settings and database health.

### API Rate Limiting
Review rate limit headers and implement backoff strategy.

## Deployment Checklist
- [ ] Run tests locally
- [ ] Review PR with teammate
- [ ] Deploy to staging
- [ ] Verify in staging
- [ ] Deploy to production
- [ ] Monitor metrics for 15 minutes
