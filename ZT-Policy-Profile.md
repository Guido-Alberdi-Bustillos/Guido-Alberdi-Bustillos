# ZT-Policy-Profile

## 1. ZTA Component Definitions

**Policy Engine (PE)** The Policy Engine is the brains. Its main function is to be the main decision maker. It doesn't directly communicate the user or the resource. The PE sees incoming security signals which are things like as user identity, device risk score, locations, etc. Then, it sets security policies to see whether access should be granted or denied.

**Policy Administrator (PA)** The Policy Administrator is the messenger of the PE. When the PE makes a decision, the PA then executes that command. It communicates with the enforcement hardware to establish or terminate a session.

**Policy Enforcement Point (PEP)** The Policy Enforcement Point is whats actively blocking a connection. This could be like a firewall or lock screen. It protects the resources by remaining locked by default, and it only opens to allow entry once it receives a command from the Policy Administrator.
