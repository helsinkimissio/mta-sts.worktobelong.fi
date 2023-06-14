# MTA STS Policy for Worktobelong.fi

This repository contains the SMTP MTA Strict Transport Security (MTA-STS) policy for Worktobelong.fi. MTA-STS is a mechanism enabling mail service providers to declare their ability to secure SMTP connections, and to specify whether sending SMTP servers should refuse to deliver to MX hosts that do not offer TLS with a matching DNS certificate.

## Current Policy

Our current MTA-STS policy is as follows:

| Tag | Value |
| --- | --- |
| version | STSv1 |
| mode | enforce |
| mx | mail.joker.com |
| max_age | 86400 |

The `mx` tag lists the current MX servers for the domain, with one server per line. This should always be kept up-to-date with the actual MX servers in use.

## MTA STS DNS Record

Our MTA-STS DNS record is as follows:

| Tag | Value |
| --- | --- |
| v | STSv1 |
| id | 202306141115 |

The `id` tag value should be updated with each policy change to signal to sending servers that they should fetch the policy again.

You can resolve the current value with the following command:

```
% host -t TXT _mta-sts.worktobelong.fi
```

This should return:

```
_mta-sts.worktobelong.fi descriptive text "v=STSv1; id=202306141115;"
```
