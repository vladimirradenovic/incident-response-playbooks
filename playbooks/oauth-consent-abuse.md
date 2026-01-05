# Incident Response Playbook: OAuth Consent Abuse / Token Theft

## Detection Triggers
- New OAuth consent granted to an application (especially high-privilege scopes)
- Admin consent performed unexpectedly or outside business hours
- New app/service principal created followed by consent or role assignment
- Unusual mailbox access patterns after consent (if applicable)

## Initial Triage (0–15 minutes)
- Identify who granted consent (user vs admin) and when
- Identify the application/service principal:
  - display name
  - publisher / verification status (if available)
  - tenant origin (internal vs external)
- Determine what permissions/scopes were granted (focus on high-impact scopes)
- Check whether the app is approved by IT/security

## Containment Actions
- Revoke OAuth consent / remove permission grants immediately if suspicious
- Disable or delete the service principal/application if not approved
- Revoke user sessions and reset credentials if account compromise is suspected
- Block sign-in for the app if applicable (Conditional Access / app control)

## Investigation Steps
- Review audit logs for:
  - consent events
  - app registrations / updates
  - role assignments
- Identify impacted resources:
  - mailbox access
  - SharePoint/OneDrive access
  - directory read/write operations (if granted)
- Search for related suspicious sign-ins:
  - new geo / new device
  - unusual client apps
- Check for persistence indicators:
  - additional consents
  - new admin roles
  - forwarding rules / inbox rules

## Recovery
- Confirm consent grants are removed and app access is blocked
- Validate user accounts are secured (password + MFA reset if needed)
- Monitor for repeated consent attempts or related sign-in anomalies
- Document the app as malicious/blocked in internal allow/deny lists

## Communication
- Notify affected users (if user consent was abused)
- Notify IT/security stakeholders and management if scope was high (mail/directory)
- If required, coordinate with legal/compliance for potential data exposure

## Lessons Learned / Improvements
- Can user consent be restricted (admin-only consent)?
- Should high-risk scopes require approval workflows?
- Do we maintain an allowlist of approved enterprise apps?
- Should detections be tuned for high-privilege scopes and admin consent events?
