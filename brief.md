Version: NAFATH-V1
Track: Software

## Overview
Nafath is a government single sign-on service that lets citizens access multiple government services through a mobile app and a website. Its central challenge is to make access convenient without weakening identity verification, security, or privacy. Because a weakness in the shared login system could affect more than one service, design decisions must be evaluated across the entire authentication journey. This brief examines six areas that matter for a trustworthy Nafath experience: authentication standards, AI risk management, Android permissions, encrypted DNS, phishing-resistant authentication, and Oman's personal data protection requirements. Each concept is linked to a practical risk and supported by authoritative references. The software question this brief focuses on is how OAuth 2.0 and OpenID Connect differ for login and delegated access.
## Software
OAuth 2.0 is an authorization framework. It lets an app get limited access to a user's resources, such as data held by another service, without receiving the user's password. OpenID Connect describes itself as "a simple identity layer on top of the OAuth 2.0 protocol." It adds an ID token that tells the app who the user is. So OpenID Connect is designed for user login, and OAuth 2.0 is designed for delegated access.

Resource: OpenID Connect Core 1.0 - https://openid.net/specs/openid-connect-core-1_0.html

## AI
Using the NIST AI Risk Management Framework (AI RMF 1.0), the authority should govern, map, measure and manage risks before launch. Key risks include inaccurate results, such as false positives that lock real citizens out or false negatives that let attackers in, and harmful bias against some groups. Other risks include weak security and resilience, privacy of login data, and lack of explainability. Human review and ongoing monitoring of flagged logins should be in place.

Resource: Artificial Intelligence Risk Management Framework (AI RMF 1.0), NIST AI 100-1 - https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf

## Mobile
Android distinguishes between install-time and runtime permissions. Normal install-time permissions are granted automatically because they provide access to data or actions that pose limited risk. Runtime permissions are required for more sensitive access, such as the camera, and the user must approve the request. The NAFATH app should request only the permissions needed for a feature, at the time they are needed, and explain why access is necessary.

Resource: Permissions on Android - https://developer.android.com/guide/topics/permissions/overview

## Networking
DNS over HTTPS (DoH) sends DNS queries inside encrypted HTTPS connections. This helps prevent parties on the network path, such as public Wi-Fi operators, from reading or modifying DNS queries in transit. However, the DoH resolver can still see the queries. DoH also does not hide the IP addresses a user connects to or secure the website or login process by itself, so HTTPS/TLS is still needed to protect application communications.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484

## Cybersecurity
An authentication method is phishing-resistant when it does not rely on the user's vigilance to avoid giving secrets to a fake site. NIST calls this verifier impersonation resistance: the login is cryptographically bound to the real site, so a fake site gets nothing useful. FIDO2/WebAuthn security keys and passkeys qualify, as do PIV smart cards. SMS codes, email codes, authenticator-app codes and push approvals do not, because users can be tricked into sharing or approving them.

Resource: NIST SP 800-63-4 - Digital Identity Guidelines - https://csrc.nist.gov/pubs/sp/800/63/4/final

## Data
Under Oman's Personal Data Protection Law (Royal Decree 6/2022), a controller must obtain the data subject's explicit consent, and prove it, unless an exception applies. It must set risk controls, notify the ministry and the data subject of breaches, appoint a data protection officer, erase data when its purpose ends, and follow rules for transfers outside Oman. Article 3 excludes some state processing, so the authority's scope must be checked.

Resource: Royal Decree 6/2022 - Issuing the Personal Data Protection Law (Consolidated) - https://decree.om/2022/l20220006/

## Misconception in My Track
A common misconception in software engineering is that OAuth 2.0 is a login protocol, so receiving an access token proves the user's identity. However, OAuth 2.0 is an authorization framework that allows an application to access protected resources; an access token is not, by itself, proof of the user's identity. OpenID Connect (OIDC) adds an identity layer on top of OAuth 2.0 and uses an ID token to convey authentication information about the user. The Introduction of OpenID Connect Core 1.0 supports this by describing OIDC as a simple identity layer on top of OAuth 2.0. This distinction matters when designing secure login systems because authorization and authentication serve different purposes.

## Open Question
I would like to learn how an app checks that an ID token is real, so it can trust that the login belongs to the right user.
