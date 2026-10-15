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

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
