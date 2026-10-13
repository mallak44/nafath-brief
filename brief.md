Version: NAFATH-V1
Track: Software

## Overview
Nafath is a government single sign-on service that lets citizens access multiple government services through a mobile app and a website. Its central challenge is to make access convenient without weakening identity verification, security, or privacy. Because a weakness in the shared login system could affect more than one service, design decisions must be evaluated across the entire authentication journey. This brief examines six areas that matter for a trustworthy Nafath experience: authentication standards, AI risk management, Android permissions, encrypted DNS, phishing-resistant authentication, and Oman's personal data protection requirements. Each concept is linked to a practical risk and supported by authoritative references. The goal is to identify design choices that protect citizens while keeping access reliable and easy to use.

## Software
OAuth 2.0 is an authorization framework. It lets an app get limited access to a user's resources, such as data held by another service, without receiving the user's password. OpenID Connect describes itself as "a simple identity layer on top of the OAuth 2.0 protocol." It adds an ID token that tells the app who the user is. So OpenID Connect is designed for user login, and OAuth 2.0 is designed for delegated access.

Resource: OpenID Connect Core 1.0 - https://openid.net/specs/openid-connect-core-1_0.html

## AI
Using the NIST AI Risk Management Framework (AI RMF 1.0), the authority should govern, map, measure and manage risks before launch and throughout the system's lifecycle. Key risks include inaccurate results, such as false positives that lock real citizens out or false negatives that let attackers in, and harmful bias against some groups. Other risks include weak security and resilience, privacy of login data, and lack of explainability. Human review and ongoing monitoring of flagged logins should be in place.

Resource: Artificial Intelligence Risk Management Framework (AI RMF 1.0), NIST AI 100-1 - https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf

## Mobile
Android distinguishes between install-time and runtime permissions. Normal install-time permissions are granted automatically because they provide access to data or actions that pose limited risk. Runtime permissions are required for more sensitive access, such as the camera, and the user must approve the request. The NAFATH app should request only the permissions needed for a feature, at the time they are needed, and explain why access is necessary.

Resource: Permissions on Android - https://developer.android.com/guide/topics/permissions/overview

## Networking

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
