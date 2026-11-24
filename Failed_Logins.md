# Failed Login Detection

## Objective

Detect excessive failed login attempts.

## Query

```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts=count()
by UserPrincipalName
| order by FailedAttempts desc
