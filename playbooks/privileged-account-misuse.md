# Incident Response Playbook: Privileged Account Misuse

## Detection Triggers
- Suspicious activity by a privileged account (admin-level actions)
- Privileged sign-ins from unusual locations, devices, or outside business hours
- Privileged account involved in MFA fatigue or OAuth abuse detections
- Unexpected changes to security controls, policies, or configurations

## Initial Triage (0–15 minutes)
- Identify the affected privileged account and role(s)
- Confirm the triggering activity:
  - sign-in details (IP, geo, device)
  - actions performed (role changes, policy updates, access grants)
- Determine if the activity was expected or authorized
- Assess potential blast radius:
  - systems accessed
  - users impacted
  - data exposure risk

## Containment Actions
- Immediately disable the privileged account if compromise is suspected
- Revoke all active sessions and tokens
- Reset credentials and MFA methods
- Remove unauthorized role assignments or configuration changes
- Isolate affected systems if changes may have introduced persistence

## Investigation Steps
- Review authentication logs for the last 24–72 hours
- Audit privileged actions:
  - role assignments
  - policy changes
  - access grants
  - audit log tampering attempts
- Check for persistence mechanisms:
  - newly created admin accounts
  - backdoor OAuth apps or service principals
  - scheduled tasks or automation changes
- Review activity across related systems (cloud, endpoints, SaaS)

## Recovery
- Restore configurations to known-good state
- Re-enable privileged account only after full validation
- Enforce stronger controls:
  - phishing-resistant MFA
  - Just-In-Time / Privileged Access Management
- Increase monitoring on privileged activity post-incident

## Communication
- Notify security leadership immediately
- Inform IT and affected system owners
- Engage legal/compliance if regulatory or data exposure risk exists
- Prepare executive-level summary if impact is significant

## Lessons Learned / Improvements
- Are privileged accounts sufficiently protected?
- Should standing admin access be reduced or eliminated?
- Are detections and alerts sufficient for privileged activity?
- Is additional logging or approval workflow required?
