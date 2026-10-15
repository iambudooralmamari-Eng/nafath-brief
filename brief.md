Version: NAFATH-V1

Track: Software

## Overview
A secure national digital login service allows citizens to access multiple government platforms using one trusted identity. Software engineering provides standardized authentication and authorization through OpenID Connect and OAuth 2.0. Artificial intelligence can identify unusual login patterns, provided its risks are assessed and monitored. Mobile security restricts access to sensitive device features through Android permissions. Networking protects DNS queries in transit using DNS over HTTPS, while recognizing its privacy limitations. Cybersecurity strengthens account protection with phishing-resistant authentication. Data governance establishes lawful processing, secure storage, and appropriate retention of personal information. These fields must work together because weaknesses in one component can undermine the entire service. Together, they support a secure, reliable, and trustworthy digital identity service.

## Software
OAuth 2.0 is an authorization framework that enables delegated access to protected resources using access tokens. OpenID Connect (OIDC) adds an identity layer for authenticating users and communicating identity claims through an ID Token. Therefore, OIDC supports user login, while OAuth 2.0 handles delegated authorization. For a national login service, the application should validate OIDC tokens and use secure authorization flows rather than treating access tokens as proof of identity.

Resource: OpenID Connect Core 1.0 incorporating errata set 2 - https://openid.net/specs/openid-connect-core-1_0-35.html

## AI
The NIST AI Risk Management Framework identifies four functions: GOVERN, MAP, MEASURE, and MANAGE. Before deployment, the authority should assess false positives that block legitimate citizens, missed attacks, biased training data, privacy exposure, adversarial manipulation, and model drift. It should validate detection performance across relevant user groups, establish accountability, document limitations, monitor operational results, and provide human review for consequential decisions. Risk management must continue after deployment.

Resource: Artificial Intelligence Risk Management Framework (AI RMF 1.0) - https://airc.nist.gov/airmf-resources/airmf/5-sec-core/

## Mobile
Android isolates applications within a sandbox and restricts sensitive resources through permissions. Dangerous permissions, such as camera or location access, generally require user approval at runtime on modern Android versions. The login application should request permission only when a relevant feature is activated, explain its purpose, and check whether permission is granted before access. If users deny permission, unrelated login functionality should remain available whenever technically possible.

Resource: Request runtime permissions - https://developer.android.com/training/permissions/requesting

## Networking
DNS over HTTPS (DoH), standardized in RFC 8484, transports DNS queries and responses through encrypted HTTPS connections. It helps prevent local network observers from reading DNS requests or modifying them in transit to a trusted resolver. However, DoH does not hide queries from the resolver, conceal destination IP addresses, or provide complete anonymity. The service must therefore combine trusted DNS resolution with HTTPS security and appropriate privacy controls.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484

## Cybersecurity
Phishing-resistant authentication cryptographically binds authentication to the legitimate verifier or protected communication channel, preventing attackers from successfully reusing captured authentication outputs at fraudulent websites. FIDO2/WebAuthn security keys and properly implemented multi-factor passkeys qualify; certificate-based smart cards using authenticated TLS can also qualify. SMS codes, email codes, and manually entered authenticator-app OTPs are not phishing-resistant because attackers can relay them during real-time phishing attacks.

Resource: NIST SP 800-63B - Authentication and Authenticator Management - https://pages.nist.gov/800-63-4/sp800-63b/authenticators/

## Data
Oman's Personal Data Protection Law, Royal Decree 6/2022, as amended by Royal Decree 68/2026, requires applicable processing to follow lawful, transparent practices, including consent unless an exception applies. Controllers and processors must implement appropriate safeguards and respect applicable data-subject rights and retention requirements. Importantly, Article 3 exempts certain government processing performed within statutory powers. The authority must therefore establish whether its specific activities fall within an exemption before determining its obligations.

Resource: Royal Decree 6/2022 Issuing the Personal Data Protection Law (Consolidated) - https://decree.om/2022/l20220006/

## Misconception in My Track
A common misconception is that OAuth 2.0 alone is a complete user authentication protocol. In reality, OAuth 2.0 primarily delegates access to protected resources; an access token does not automatically establish the identity of the person using an application. OpenID Connect adds standardized authentication capabilities, including ID Tokens containing identity claims. Section 1.1, "OpenID Connect Core 1.0 Overview," explains that OIDC is an identity layer built on OAuth 2.0. For a national single sign-on platform, confusing authorization with authentication could cause applications to accept inappropriate tokens as proof of login, creating security vulnerabilities.


## Open Question
How should the authority design and test an OpenID Connect session-management and logout strategy that securely coordinates authentication across multiple government applications while minimizing the risk of token theft, session hijacking, and unintended access?
