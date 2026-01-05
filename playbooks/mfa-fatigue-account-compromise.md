# Incident Response Playbook: MFA Fatigue / Account Compromise

## Detection Triggers
- Multiple authentication failures followed by a successful sign-in
- MFA push spamming reported by the user
- Correlation with impossible travel or new device sign-in
- Conditional Access or Identity Protection risk alerts (if available)

## Initial Triage (0–15 minutes)
- Identify affected user and role (standard vs privileged)
- Confirm sign-in details:
  - IP address
  - geo/location
  - device
  - client application
- Determine whether MFA approval was expected or accidental
- Check if similar patterns are affecting other users

## Containment Actions
- Revoke all active sessions for the user
- Force password reset
- Reset MFA methods
- Temporarily block suspicious IP addresses
- Disable account immediately if compromise is confirmed or user is privileged

## Investigation Steps
- Review authentication logs for the last 24–48 hours
- Check for:
  - impossible travel patterns
  - sign-ins from new devices
  - unusual client applications
- Review OAuth consent grants and app registrations
- Check mailbox rules, forwarding, and inbox access
- Review recent administrative or sensitive actions (if applicable)

## Recovery
- Re-enable account after credential hygiene is complete
- Enforce phishing-resistant MFA if available
- Confirm no persistence mechanisms remain
- Monitor account activity closely for the next 24–72 hours

## Communication
- Notify the affected user with a clear explanation
- Notify security and IT stakeholders
- Escalate to management if privileged access or sensitive data was involved

## Lessons Learned / Improvements
- Were MFA fatigue patterns detected early enough?
- Are Conditional Access policies sufficient?
- Should detection thresholds or exclusions be tuned?
- Is phishing-resistant MFA required for this user group?
