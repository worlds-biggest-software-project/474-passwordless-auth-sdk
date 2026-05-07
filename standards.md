# Standards & API Reference

> Project: Passwordless Auth SDK · Candidate #474 · Generated: 2026-05-07

---

## Industry Standards & Specifications

### W3C Standards

**Web Authentication (WebAuthn) Level 2**
- URL: https://www.w3.org/TR/webauthn-2/
- W3C Recommendation published 8 April 2021. Defines the browser-side JavaScript API (`navigator.credentials.create()` and `navigator.credentials.get()`) that relying parties call to register and authenticate public-key credentials. Level 2 adds features including large-blob storage and the credProps extension. Any SDK that exposes passkey flows wraps this API.

**Web Authentication (WebAuthn) Level 3**
- URL: https://www.w3.org/TR/webauthn-3/
- W3C Candidate Recommendation Snapshot (January 2026). Adds the `getClientCapabilities()` method for feature detection, the `related-origins` mechanism for multi-origin relying parties, and `hints` to guide authenticator selection. SDKs targeting 2026+ deployments should track this draft.

**Credential Management Level 1**
- URL: https://www.w3.org/TR/credential-management-1/
- W3C Recommendation. Defines the `navigator.credentials` interface and the abstract `Credential` base class from which `PublicKeyCredential` (WebAuthn/passkeys), `PasswordCredential`, and `FederatedCredential` all inherit. Essential reading for any SDK that integrates browser-native credential storage and autofill.

**Digital Credentials API**
- URL: https://www.w3.org/TR/digital-credentials/
- W3C Working Draft (2025–2026). Extends Credential Management to support the presentation of verifiable credentials and mobile driving licences (ISO 18013-5 mDL). Relevant for future step-up or identity-verification scenarios within a passwordless SDK.

### FIDO Alliance Specifications

**FIDO2: Client to Authenticator Protocol (CTAP) 2.1 / 2.2**
- URL: https://fidoalliance.org/specifications/
- FIDO Alliance Standard. CTAP defines the protocol used between a browser/platform and a roaming authenticator (USB, NFC, BLE hardware key or mobile device). CTAP 2.2 adds hybrid transport (phone-as-authenticator), biometric enrollment and management RPCs, and enhanced enterprise attestation. Passwordless SDKs that support cross-device passkeys depend on CTAP 2.2 behaviour abstracted by the platform.

**FIDO2 Passkeys Specification (combined WebAuthn + CTAP)**
- URL: https://passkeys.dev/docs/reference/specs/
- The passkeys.dev reference maintained by the W3C WebAuthn Adoption Community Group collates the WebAuthn and CTAP specs alongside platform-specific notes for iOS, Android, Windows, and macOS. Practical starting point for SDK implementors needing a single-source specification reference.

### IETF / RFC Standards

**RFC 6749 — The OAuth 2.0 Authorization Framework**
- URL: https://datatracker.ietf.org/doc/html/rfc6749
- Foundation protocol for delegated authorisation. Passwordless SDKs typically issue short-lived access tokens and refresh tokens under OAuth 2.0 conventions, and support the Authorization Code flow for integrating third-party IdPs alongside passwordless methods.

**RFC 7636 — Proof Key for Code Exchange (PKCE)**
- URL: https://datatracker.ietf.org/doc/html/rfc7636
- Mandatory extension to the Authorization Code flow for public clients (SPAs, mobile apps). Prevents authorisation-code interception attacks. All current best-practice guidance requires PKCE for any OAuth 2.0 client that cannot securely store a client secret.

**RFC 7519 — JSON Web Token (JWT)**
- URL: https://datatracker.ietf.org/doc/html/rfc7519
- Defines the compact, URL-safe claims representation used ubiquitously for session and access tokens in passwordless authentication systems. SDKs must issue and validate JWTs that conform to this specification.

**RFC 8725 — JSON Web Token Best Current Practices (BCP 225)**
- URL: https://www.rfc-editor.org/rfc/rfc8725.html
- Published February 2020. Updates RFC 7519 with actionable security guidance: algorithm verification, sufficient key entropy, audience and issuer validation, and prevention of cross-JWT confusion attacks. SDK-issued tokens must comply with these best practices.

**RFC 8628 — OAuth 2.0 Device Authorization Grant**
- URL: https://datatracker.ietf.org/doc/html/rfc8628
- Enables OAuth flows on input-constrained devices (CLIs, smart TVs, IoT) by directing users to a secondary device for authentication. Relevant for passwordless SDKs targeting developer CLI tools or embedded environments.

**RFC 6238 — TOTP: Time-Based One-Time Password Algorithm**
- URL: https://www.rfc-editor.org/rfc/rfc6238.html
- Standardises the time-based variant of HMAC-OTP (HOTP). Forms the basis of all authenticator-app TOTP flows (Google Authenticator, Authy, etc.). A passwordless SDK offering TOTP as a step-up or fallback factor must implement this RFC.

**RFC 4226 — HOTP: An HMAC-Based One-Time Password Algorithm**
- URL: https://datatracker.ietf.org/doc/html/rfc4226
- Base standard for HMAC-derived one-time passwords. RFC 6238 (TOTP) is a time-based extension of this specification. Required reading when implementing any OTP generation or validation logic.

**RFC 8414 — OAuth 2.0 Authorization Server Metadata**
- URL: https://datatracker.ietf.org/doc/html/rfc8414
- Defines the `/.well-known/oauth-authorization-server` discovery endpoint. Enables clients to auto-configure OAuth flows by fetching supported grants, endpoints, and algorithms — important for SDK ease-of-integration.

**RFC 9700 — Best Current Practice for OAuth 2.0 Security**
- URL: https://datatracker.ietf.org/doc/rfc9700/
- January 2025. Consolidates OAuth 2.0 security recommendations: mandate PKCE for all clients, restrict redirect URIs, avoid implicit flow, and require sender-constrained tokens where possible. Supersedes earlier OAuth security advice.

**RFC 8471 — The Token Binding Protocol Version 1.0**
- URL: https://datatracker.ietf.org/doc/html/rfc8471
- Enables cryptographic binding of OAuth/OIDC tokens to a specific TLS connection, making stolen tokens useless for replay. Browser support was removed by major vendors; included here as background for SDK threat-model documentation.

### OpenID Foundation Standards

**OpenID Connect Core 1.0**
- URL: https://openid.net/specs/openid-connect-core-1_0.html
- The primary identity layer on top of OAuth 2.0. Defines ID tokens, UserInfo endpoint, and standard claim names. Passwordless SDKs are typically OIDC-compliant identity providers so that developers can integrate them with downstream apps using standard OIDC discovery.

**OpenID Connect Discovery 1.0**
- URL: https://openid.net/specs/openid-connect-discovery-1_0.html
- Defines the `/.well-known/openid-configuration` metadata endpoint. Allows client apps and partner services to discover a passwordless SDK's endpoints, supported scopes, and signing keys without manual configuration.

**OpenID Connect Client-Initiated Backchannel Authentication (CIBA) Core 1.0**
- URL: https://openid.net/specs/openid-client-initiated-backchannel-authentication-core-1_0.html
- Final Specification. Enables authentication flows where the user completes authentication on a separate "authentication device" (e.g., mobile push notification) rather than the consumption device. Directly applicable to push-based passwordless flows and out-of-band magic-link delivery.

**OAuth 2.1 (draft)**
- URL: https://datatracker.ietf.org/doc/draft-ietf-oauth-v2-1/
- Consolidates OAuth 2.0 with all subsequent security RFCs: PKCE is required, implicit flow removed, refresh token rotation mandated. SDKs building against current best practice should align with OAuth 2.1 semantics even before final publication.

### Security & Compliance Frameworks

**NIST SP 800-63B-4 — Digital Identity Guidelines: Authentication and Authenticator Management**
- URL: https://csrc.nist.gov/pubs/sp/800/63/b/4/final
- Final July 2025. Defines three Authenticator Assurance Levels (AAL1–AAL3). Passkeys (both device-bound and syncable) are explicitly integrated into AAL2 and AAL3 requirements. A companion supplement (SP 800-63Bsup1) addresses syncable passkeys specifically. SDK documentation should map supported authentication methods to their AAL rating.

**NIST SP 800-63Bsup1 — Incorporating Syncable Authenticators into NIST SP 800-63B**
- URL: https://csrc.nist.gov/pubs/sp/800/63/b/4/final (companion document)
- Provides specific guidance on cloud-synced passkeys (e.g., iCloud Keychain, Google Password Manager), clarifying that syncable passkeys satisfy AAL2 when account-recovery controls are in place. Critical for SDK documentation targeting regulated industries.

**OWASP Authentication Cheat Sheet**
- URL: https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html
- OWASP living document covering secure authentication implementation: rate limiting, account lockout, credential stuffing mitigation, and passkey integration guidance. Provides implementation-level security requirements that an SDK should satisfy by default.

**OWASP Multifactor Authentication Cheat Sheet**
- URL: https://cheatsheetseries.owasp.org/cheatsheets/Multifactor_Authentication_Cheat_Sheet.html
- Covers acceptable second-factor methods, implementation pitfalls for TOTP and OTP flows, and guidance on phishing resistance. Directly relevant to step-up and fallback authentication in a passwordless SDK.

**ISO/IEC 27001:2022 — Information Security Management (Annex A.5.16 & A.5.17)**
- URL: https://www.iso.org/information-security/identity-management
- The primary international information security standard. Annex A.5.16 governs the full lifecycle of digital identities; A.5.17 mandates formal management of authentication information (passwords, PINs, biometrics, tokens). SDK deployments in enterprise and regulated contexts will be evaluated against these controls.

---

## Similar Products — Developer Documentation & APIs

### Auth0 (Okta)
- **Description:** Market-leading CIAM platform with native passkey support across all tiers, 7,000+ social/enterprise integrations, and a comprehensive management API for users, tenants, and authentication flows.
- **API Documentation:** https://auth0.com/docs/api/authentication
- **Native Passkeys API:** https://auth0.com/docs/native-passkeys-api
- **SDKs/Libraries:** JavaScript (`@auth0/auth0-spa-js`), React (`@auth0/auth0-react`), Node.js (`auth0`), Python, Go, iOS, Android — https://auth0.com/docs/libraries
- **Developer Guide:** https://auth0.com/docs
- **Standards:** OIDC, OAuth 2.0, SAML 2.0, WebAuthn/FIDO2, OpenAPI-documented REST API
- **Authentication:** OAuth 2.0 client credentials, Management API tokens (JWT)

### Stytch
- **Description:** Developer-first authentication platform offering passkeys, magic links, email OTP, SMS OTP, TOTP, and biometric logins via headless APIs and a configurable pre-built UI.
- **API Documentation:** https://stytch.com/docs
- **SDKs/Libraries:** `@stytch/vanilla-js`, `@stytch/react`, Node.js backend SDK, Python, Go, Ruby, iOS, Android, React Native
- **Developer Guide:** https://stytch.com/docs/guides
- **Standards:** REST/JSON, OAuth 2.0, OpenID Connect, WebAuthn
- **Authentication:** Project-scoped secret key (Bearer token) for backend; publishable key for frontend SDKs

### Descope
- **Description:** No-code/low-code CIAM platform with a drag-and-drop flow builder for composing passwordless authentication sequences. Supports passkeys, magic links, OTP, TOTP, and SSO.
- **API Documentation:** https://docs.descope.com/
- **SDKs/Libraries:** JavaScript, React, Vue, Angular, Node.js, Python, Go, Java, .NET, iOS, Android, React Native, Flutter
- **Developer Guide:** https://docs.descope.com/getting-started
- **Standards:** OIDC, OAuth 2.0, SAML 2.0, WebAuthn, REST/JSON
- **Authentication:** Project ID + management key (Bearer token)

### Passage by 1Password
- **Description:** Passkey-first authentication SDK designed for rapid integration. Offers a lightweight footprint, Passkey Flex (add passkeys to existing auth) and Passkey Complete (full standalone auth) product lines.
- **API Documentation:** https://docs.passage.id/flex/apis
- **SDKs/Libraries:** Passkey Flex JavaScript SDK (`@passageidentity/passage-flex-js`), Python (`passage-identity`), Go backend SDK, iOS SDK
- **Developer Guide:** https://docs.passage.id/
- **Standards:** WebAuthn/FIDO2, JWT, REST/JSON
- **Authentication:** API key (console-generated) for backend SDKs; frontend SDK uses public app ID

### Hanko
- **Description:** Open-source, self-hostable passkey authentication stack. Provides a Go-based backend service, pre-built web components (`hanko-auth`, `hanko-profile`), and a hosted Passkey API for layering passkeys onto existing auth systems.
- **API Documentation:** https://docs.hanko.io/passkey-api/introduction
- **SDKs/Libraries:** `@teamhanko/hanko-elements` (web components), JavaScript frontend SDK, Go SDK; GitHub: https://github.com/teamhanko/hanko
- **Developer Guide:** https://docs.hanko.io/
- **Standards:** WebAuthn/FIDO2, OIDC, JWT, REST/JSON, OpenAPI
- **Authentication:** API secret for Hanko Cloud; self-hosted deployments use configurable secrets

### Clerk
- **Description:** Developer-focused identity platform with drop-in React/Next.js components and a headless JavaScript SDK. Passkeys are supported alongside passwords, social login, and Web3 authentication.
- **API Documentation:** https://clerk.com/docs/reference
- **Passkey Custom Flows:** https://clerk.com/docs/guides/development/custom-flows/authentication/passkeys
- **SDKs/Libraries:** `@clerk/clerk-react`, `@clerk/nextjs`, `@clerk/clerk-js`, iOS, Android, Flutter, Expo
- **Developer Guide:** https://clerk.com/docs/react/getting-started/quickstart
- **Standards:** OIDC, OAuth 2.0, WebAuthn, JWT, REST/JSON
- **Authentication:** Publishable key for frontend; secret key for backend API calls

### MojoAuth
- **Description:** Passwordless authentication platform focused on magic links, email OTP, and SMS OTP, with passkey support added. API-first design with a broad SDK catalogue.
- **API Documentation:** https://docs.mojoauth.com/
- **SDKs/Libraries:** JavaScript, Node.js, Go, PHP, Java, .NET, Python, iOS, Android — https://github.com/MojoAuth
- **Developer Guide:** https://docs.mojoauth.com/guides/html-and-js/
- **Standards:** OIDC, OAuth 2.0, SAML 2.0, FIDO2, REST/JSON
- **Authentication:** API key from MojoAuth dashboard

### WorkOS
- **Description:** Enterprise-focused identity platform offering SSO, Directory Sync, and User Management including passwordless authentication. Provides an OpenAPI-documented REST API and official multi-language SDKs.
- **API Documentation:** https://workos.com/docs/reference
- **OpenAPI Spec:** https://github.com/workos/openapi-spec
- **SDKs/Libraries:** Node.js, Python, Ruby, Go, .NET, PHP, Java
- **Developer Guide:** https://workos.com/docs
- **Standards:** SAML 2.0, OIDC, OAuth 2.0, WebAuthn, OpenAPI 3.x
- **Authentication:** API key (secret key) for all server-side SDK calls

### Supabase Auth
- **Description:** Open-source BaaS authentication module supporting magic links, email OTP, social OAuth, and TOTP MFA. Native passkey support is not yet built in; third-party passkey providers (e.g., Passage) are used for passkey workflows.
- **API Documentation:** https://supabase.com/docs/guides/auth
- **JavaScript Reference:** https://supabase.com/docs/reference/javascript/v1/auth-signin
- **SDKs/Libraries:** `@supabase/supabase-js`, Flutter/Dart SDK, Swift, Kotlin
- **Developer Guide:** https://supabase.com/docs/guides/auth/auth-email-passwordless
- **Standards:** OIDC, OAuth 2.0, JWT, REST/JSON, OpenAPI
- **Authentication:** `anon` public key for client; `service_role` secret key for server operations

### passkeys.dev (FIDO Alliance / W3C Community Resource)
- **Description:** Authoritative developer resource maintained by the W3C WebAuthn Adoption Community Group. Aggregates specifications, platform support matrices, library listings, and a live WebAuthn capability tester.
- **Reference Documentation:** https://passkeys.dev/docs/reference/
- **Specification Index:** https://passkeys.dev/docs/reference/specs/
- **Developer Tools:** https://tools.passkeys.dev/
- **Standards:** WebAuthn Level 2 & 3, CTAP 2.1/2.2, FIDO2
- **Authentication:** N/A — reference resource, not an API product

---

## Notes

**Emerging standards to watch:**

- **OAuth 2.1** (draft-ietf-oauth-v2-1) is expected to reach RFC status in 2026 and will be the definitive reference for new SDK token flows.
- **W3C Digital Credentials API** extends Credential Management to verifiable credentials (VCs) and mobile driving licences; watch for intersection with identity verification step-up flows.
- **WebAuthn Level 3** is a Candidate Recommendation as of January 2026; the `related-origins` feature is particularly valuable for multi-domain product suites sharing a passkey namespace.
- **NIST SP 800-63-4** (July 2025) is now final and supersedes SP 800-63-3; SDK compliance documentation should reference the -4 revision.

**Platform-specific passkey implementation guides** (supplement to specifications above):
- Apple Passkeys: https://developer.apple.com/passkeys/
- Google Passkeys for Android/Web: https://developers.google.com/identity/passkeys/developer-guides
- Microsoft Windows Hello / FIDO2: https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/
