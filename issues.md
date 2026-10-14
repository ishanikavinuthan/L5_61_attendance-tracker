# Lab 5: Static Code Analysis — Issues and Fixes

## Issues Identified and Fixed

| Issue | Type | Original Line(s) | Description | Fix Approach |
|---|---|---|---|---|
| Mutable default argument | Bug | 18 | Using an empty dictionary as a default argument can result in shared mutable state between calls. | Changed the default to None and initialized a dictionary inside the function when needed. |
| Attendance eligibility condition | Bug | 30 | The original condition used > instead of >=, making exactly 75% attendance ineligible. | Changed the condition to percentage >= MIN_ATTENDANCE. |
| SSL certificate verification disabled | Security | 60 | verify=False disables SSL certificate verification for the ERP request. | Removed verify=False to retain certificate verification. |
| Missing HTTP request timeout | Reliability | 60 | Without a timeout, an HTTP request could wait indefinitely. | Added timeout=10 to requests.post(). |
| Shell-based backup command | Security | 64 | The original backup used subprocess.Popen with shell=True. | Replaced the shell command with Python's tarfile module. |
| Legacy TLS configuration | Security | 66 | The original function used ssl.PROTOCOL_TLSv1. | Replaced it with ssl.create_default_context(). |
| Reminder command configuration | Security | 73 | The original reminder configuration used a command string with shell=True. | Changed it to a list of arguments and shell=False. |
| Code formatting | Style | Multiple | Flake8 reported excessive line lengths and incorrect blank-line formatting. | Reformatted the code to follow the configured style rules. |

Note: Line numbers refer to the original source before fixes.

## Verification

- The program executed successfully after the changes.
- The eligibility check returned True for 75% attendance.
- Bandit reported no security issues in the final scan.
- Flake8 completed without reporting style violations.
- The Pylint score improved from 4.55/10 to 6.05/10.

## Conclusion

Static code analysis helped identify security risks, a mutable default argument, an incorrect eligibility condition, and style violations. The fixes improved the program's security, correctness, and readability.
