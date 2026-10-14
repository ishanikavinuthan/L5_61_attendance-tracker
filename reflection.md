# Lab 5: Static Code Analysis — Reflection

## 1. Which issues were the easiest to fix, and which were the hardest? Why?

The easiest issues to fix were the formatting violations and the incorrect attendance eligibility condition. Formatting issues could be corrected using autopep8, while the eligibility issue required changing the comparison from > to >=. The harder issues were the security-related ones because they required understanding how SSL verification, HTTP timeouts, TLS configuration, and shell command execution affect security and reliability.

## 2. Did the static analysis tools report any false positives? If so, describe one example.

The initial Bandit report flagged the import of the subprocess module. Importing subprocess alone does not necessarily create a vulnerability, so that warning can be considered a possible false positive when viewed in isolation. However, the original program also used subprocess with shell=True, which justified further investigation. Therefore, the broader security concern was valid. The final Bandit scan reported no issues.

## 3. How would you integrate static analysis tools into your actual software development workflow?

I would run Pylint, Bandit, and Flake8 regularly while developing Python applications. I would run them before committing changes and could also configure them in a pre-commit hook or a CI pipeline so that code is checked automatically when changes are pushed. This would help identify bugs, security risks, and style issues early.

## 4. What tangible improvements did you observe in the code quality, readability, or potential robustness after applying the fixes?

The eligibility check now correctly treats exactly 75% attendance as eligible. The mutable default argument was replaced with None, the ERP request now has a timeout and retains SSL certificate verification, and the backup function no longer uses a shell-based subprocess command. The reminder configuration was also changed to use a list of arguments with shell=False. Formatting improvements eliminated the reported Flake8 violations. The Pylint score increased from 4.55/10 to 6.05/10, and the final Bandit scan reported no security issues.
