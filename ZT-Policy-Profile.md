# ZT-Policy-Profile

## 1. ZTA Component Definitions

**Policy Engine (PE)** The Policy Engine is the brains. Its main function is to be the main decision maker. It doesn't directly communicate the user or the resource. The PE sees incoming security signals which are things like as user identity, device risk score, locations, etc. Then, it sets security policies to see whether access should be granted or denied.

**Policy Administrator (PA)** The Policy Administrator is the messenger of the PE. When the PE makes a decision, the PA then executes that command. It communicates with the enforcement hardware to establish or terminate a session.

**Policy Enforcement Point (PEP)** The Policy Enforcement Point is whats actively blocking a connection. This could be like a firewall or lock screen. It protects the resources by remaining locked by default, and it only opens to allow entry once it receives a command from the Policy Administrator.


## 2. Core Principle Application

**Chosen Principle:** Verify Explicitly

Verify Explicitly means the system should never asume that a user is safe just because they are on the internal network or have logged in once before. Every single access request must be authenticated before access is granted.

At the Golden State Water Treatment Facility, the PE enforces this by checking every request to the HR Employee PII Database. For example, if an HR manager attempts to access an employees background checks, the PE checks not only username and password, but also signals like the geographical location of the user and the time of day. If the request came from an unrecognized IP address outside of California in the middle of the night, then the PE denies the request even if the credentials are correct. This is because the explicit context of the request does not meet certain security requirements.



## 3. Simplified Policy Table

| Policy Requirement (Signal) | Condition to be Met by User | Action if Condition is Met |
| :--- | :--- | :--- |
| **User Identity** | User must be authenticated via Phishing-Resistant MFA and belong to the 'HR_Staff' group. | Grant Access |
| **Device Posture** | Device must be a corporate-managed asset with an up-to-date EDR agent and disk encryption enabled. | Grant Access |
| **Network Context** | Connection must originate from a verified Facility IP or a managed Global Secure Access tunnel. | Grant Access |
