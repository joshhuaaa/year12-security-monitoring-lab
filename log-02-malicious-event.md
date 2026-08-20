
# Log 02 — Simulated Suspicious Authentication Activity

## Event observed

I investigated a simulated security log containing a sequence of authentication and system activity events.

The log contained  events:

```text
SECURITY LAB — SIMULATED LOG 02
Scenario: Suspicious Authentication Activity
Status: SIMULATED — NOT A REAL INCIDENT

2026-08-20 14:31:02  AUTH_FAILURE   User=admin   Source=10.0.0.50
2026-08-20 14:31:08  AUTH_FAILURE   User=admin   Source=10.0.0.50
2026-08-20 14:31:14  AUTH_FAILURE   User=admin   Source=10.0.0.50
2026-08-20 14:31:21  AUTH_SUCCESS   User=admin   Source=10.0.0.50
2026-08-20 14:32:03  PROCESS_ALERT  Process=PowerShell
2026-08-20 14:32:17  FILE_MODIFIED  File=system_config.txt
```

### Initial assessment

The first three events show repeated failed authentication attempts against the `admin` account from the same source.

Then a few moments later access was granted for the user / possible threat actor.

After this, PowerShell activity was detected and a configuration file was modified.

The sequence of events is  suspicious because several different types of activity occurred in a short period of time.

### Security assessment

The repeated authentication failures followed by a successful login could indicate an attempt to gain access to an account.

The PowerShell activity and file modification increase the level of concern because they occurred shortly after the successful authentication.

However, this isn't a real scenario so the events do not represent a real attack.

In a real investigation, additional evidence would be required before confirming that the activity was malicious. However due to config file modifications you have grounds to start acting.

### What I learned

This investigation demonstrated the importance of:

* Analysing events in chronological order
* Identifying repeated authentication failures
* Investigating successful logins following failed attempts
* Examining activity that occurs after authentication
* Looking for connections between multiple events
* Distinguishing suspicious activity from confirmed malicious activity

### Conclusion

The simulated activity would be classified as **suspicious and requiring further investigation**.

The combination of repeated authentication failures, a successful login, PowerShell activity and a file modification creates a pattern that a security analyst would investigate further.

In a real environment, the analyst would collect additional logs and evidence to determine whether the activity was legitimate or malicious.
