# Passwordless Authentication SDK — Feature & Functionality Survey

> Candidate #474 · Researched: 2026-05-03

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| Auth0 by Okta | Commercial SaaS | Proprietary | https://auth0.com |
| Descope | Commercial SaaS | Proprietary | https://www.descope.com |
| Passage by 1Password | Commercial SaaS / SDK | Proprietary | https://passage.1password.com |
| Stytch | Commercial SaaS (acquired by Twilio 2025) | Proprietary | https://stytch.com |
| MojoAuth | Commercial SaaS | Proprietary | https://mojoauth.com |
| Clerk | Commercial SaaS | Proprietary | https://clerk.com |
| Okta Workforce Identity | Commercial SaaS | Proprietary | https://www.okta.com/products/workforce-identity/ |
| Hanko | Open Source & Managed SaaS | Apache 2.0 / AGPL | https://www.hanko.io |
| Supabase Auth | Open Source | MIT and Apache 2.0 | https://supabase.com |
| Keycloak | Open Source | Apache 2.0 | https://www.keycloak.org |

## Feature Analysis by Solution

### Auth0 by Okta

**Core features**
- Native passkey support (FIDO2/WebAuthn) available on all plans, including free tier
- Magic link authentication with fallback OTP for blocked link clicks
- SMS and TOTP one-time passcodes with authenticator app integration
- Device biometrics (Face ID, Touch ID, Windows Hello) as authenticators
- Social and enterprise SSO (OAuth 2.0/OIDC) with 7,000+ pre-built integrations
- Drop-in authentication UI components for web and native (iOS/Android/React Native/Flutter)
- Session management with short-lived JWTs and refresh-token rotation
- Adaptive MFA with risk-based authentication and progressive enrollment
- Device session listing and remote revocation
- Admin dashboard with authentication adoption metrics, drop-off funnels, failed attempts
- User management console and bulk operations

**Differentiating features**
- 7,000+ pre-built integrations with third-party services (unmatched breadth)
- Adaptive MFA triggered by risk signals
- Progressive enrollment workflow for existing password users
- Managed at scale across enterprise customer base
- Deep Atlassian (Okta) ecosystem integration

**UX patterns**
- Unified Login page (Universal Login) as web-native option
- Native SDKs for mobile with biometric integration
- Progressive complexity: basic passwordless on free tier; advanced MFA on paid
- Pre-built components reduce custom UI work

**Integration points**
- 7,000+ marketplace integrations (SIEM, fraud detection, analytics, etc.)
- OAuth 2.0/OIDC provider capabilities
- Rules engine for custom workflows
- SAML 2.0 for enterprise IdPs
- RESTful API and SDKs

**Known gaps**
- No self-hosting option; SaaS-only
- Largest organizations may find pricing model less favorable at scale
- Marketplace integrations require manual configuration
- No UI for A/B testing authentication flows

**Licence / IP notes**
- Proprietary; owned by Okta as of 2023


### Descope

**Core features**
- No-code drag-and-drop authentication flow builder
- Full authentication method support: passkeys, magic links, OTP (email/SMS), biometrics, social logins
- Customizable signup, login, MFA, SSO, and step-up authentication flows
- Multi-tenancy with per-tenant branding customization
- B2B and B2C support with org-level access management
- A/B testing for authentication methods with step-by-step drop-off analytics
- Progressive enrollment from passwords to passwordless
- MFA triggers based on risk signals
- Self-service SSO setup for enterprise IdPs
- Flexible integration: no-code flows, SDKs/APIs, or hybrid

**Differentiating features**
- No-code flow builder (reduces developer effort significantly)
- Zero-code changes to flows without redeploying
- Enterprise-friendly B2B features (multi-tenancy, org management)
- A/B testing with granular flow analytics
- Generous free tier for developers

**UX patterns**
- Visual flow composition with drag-and-drop
- Real-time preview of flows during design
- Configuration-over-code philosophy
- Pre-built templates for common flows
- Progressive disclosure of advanced options

**Integration points**
- Extensible through webhooks for custom logic
- SDKs for web, mobile, and backend
- OAuth 2.0/OIDC provider capabilities
- SSO connectors (SAML 2.0, OIDC)
- SCIM provisioning for identity sync

**Known gaps**
- Smaller integration ecosystem vs. Auth0
- UI customization limited by no-code paradigm
- Less mature B2B feature set vs. specialist platforms
- Limited advanced analytics vs. dedicated risk providers

**Licence / IP notes**
- Proprietary; funded (Series A, multiple rounds)


### Passage by 1Password

**Core features**
- Passkey-first SDK treating passwords as deprecated legacy option
- Native iOS SDK with state-of-the-art passkey support (iOS 16+)
- Flexible magic links for iOS 14+ with fallback for older devices
- Multiple SDK variants: Passage Complete, Passage for Android, Passkey Flex
- Drop-in UI components handling full passwordless login flow
- Integrates with 1Password ecosystem for passkey synchronization
- Web and native mobile (iOS/Android/React Native) support
- Simplified WebAuthn complexity via SDK abstractions

**Differentiating features**
- Passkey-first philosophy (no password fallback in default config)
- Deep 1Password ecosystem integration
- Lightweight SDK footprint ideal for product teams
- Native experience without relying on browser WebView (on mobile)
- Simplified cross-device passkey sync

**UX patterns**
- Minimal-friction passkey registration
- Device-bound credential prompting
- Biometric unlock experience
- Fallback to magic links for unsupported devices
- Drop-in component model for rapid integration

**Integration points**
- 1Password integration for passkey storage and sync
- SDKs for web, iOS, Android, React Native
- RESTful API for custom implementations
- OAuth 2.0/OIDC support
- Limited third-party ecosystem integration (1Password-focused)

**Known gaps**
- Limited to passkey and magic link (no SMS OTP or TOTP natively)
- Smaller ecosystem integration vs. Auth0 or Stytch
- No-code flow builder not available
- Less suitable for large enterprise workflows requiring SSO

**Licence / IP notes**
- Proprietary; owned by 1Password


### Stytch

**Core features**
- API-first developer platform with clean, comprehensive REST API
- Passwordless-first: magic links, OTP (email/SMS/WhatsApp), passkeys, biometrics as default
- OAuth 2.0/OIDC integrations (Google, Facebook, GitHub, etc.)
- B2B SSO with Organizations API for multi-tenant user management
- SCIM provisioning for identity sync with enterprise IdPs
- Session management with device fingerprinting and anomaly detection
- Enterprise-grade security: bot protection, breached password detection, adaptive MFA
- IP allow/block lists and advanced fraud detection
- Pre-built frontend components and headless SDKs for fine-grained control
- Mobile SDKs for iOS and Android

**Differentiating features**
- API-first design philosophy (vs. UI-first competitors)
- Strong B2B feature set (Organizations, SCIM, SSO) developed post-2023
- Comprehensive fraud detection and bot protection suite
- Flexible frontend options: headless API, pre-built components, or hybrid
- Acquired by Twilio (November 2025) providing enterprise backing

**UX patterns**
- Headless-by-default: maximum control over user experience
- Pre-built components optional for rapid implementation
- Progressive complexity: simple magic link to advanced B2B flows
- Mobile-native SDKs for native app development

**Integration points**
- Comprehensive REST API with fine-grained controls
- Multiple OAuth 2.0/OIDC providers
- B2B APIs for multi-tenant management
- SCIM 2.0 provisioning
- Webhook system for custom workflows
- SDKs for web, mobile, and backend

**Known gaps**
- Complex learning curve due to API-first design
- No visual flow builder (requires code for advanced flows)
- Smaller integration marketplace vs. Auth0
- Recently acquired; integration strategy under Twilio's governance uncertain

**Licence / IP notes**
- Proprietary; acquired by Twilio on November 14, 2025


### MojoAuth

**Core features**
- Unified API for OTP, Magic Links, Passkeys, and SSO
- Email, SMS, WhatsApp, and TOTP one-time passcode delivery
- Magic links with configurable expiration and single-use enforcement
- Passkey support (FIDO2/WebAuthn) as high-security option
- Social login integrations (Google, Facebook, GitHub, etc.)
- Email infrastructure optimization (handles delivery reliability)
- Rate limiting and suspicious IP throttling to prevent abuse
- Drop-in UI components for web and mobile
- Production-ready implementation in ~1 day per method

**Differentiating features**
- Multi-method flexibility in single API (all OTP types, magic links, passkeys)
- Email infrastructure expertise (addresses delivery reliability issues)
- Fast implementation time with pre-built components
- Support ticket reduction (80% claimed improvement)
- Conversion improvement metrics

**UX patterns**
- Simple, straightforward API for each authentication method
- Quick integration with pre-built flows
- Email-first for initial user acquisition
- Progressive enrollment to stronger methods
- Fallback chains (passkey → magic link → email OTP)

**Integration points**
- RESTful API with consistent method interfaces
- Pre-built UI components for web
- Email and SMS delivery infrastructure
- Webhook support for custom logic
- Social OAuth integrations

**Known gaps**
- Limited B2B/enterprise features (no multi-tenancy, SAML, SCIM)
- Smaller ecosystem compared to Auth0 or Stytch
- No-code flow builder not available
- Limited advanced analytics

**Licence / IP notes**
- Proprietary; VC-funded startup


### Clerk

**Core features**
- Passkey support with simple dashboard toggle
- One-line component integration for passkey management
- Users can manage up to 10 passkeys per account
- Phishing-resistant authentication via local biometric unlock
- Pre-built <UserProfile /> component with Security tab
- Passkey platform sync across user devices
- Additional passwordless methods: OTP, custom authentication links, social sign-in
- User management and organization/team management
- Session management and multi-device support
- Core 3 release (March 2026) with updated pricing and features

**Differentiating features**
- Passkey management in pre-built components (not custom-coded)
- Simple, frictionless passkey setup (toggle enablement)
- Deep integration with modern web frameworks
- Developer-friendly pricing model (free tier generous)
- Regular feature releases (Core 3 in March 2026)

**UX patterns**
- Component-first architecture (React-native components)
- Minimal configuration for passkeys (UI handles complexity)
- User self-service for passkey management
- Progressive enrollment from passwords to passkeys

**Integration points**
- React, Next.js, and other framework integration
- Custom flows for advanced scenarios
- OAuth 2.0/OIDC support
- Pre-built webhook system
- Limited enterprise integrations documented

**Known gaps**
- Less suitable for headless implementations
- Smaller B2B feature set vs. enterprise platforms
- Limited flow builder flexibility
- No self-hosting option

**Licence / IP notes**
- Proprietary; backed by venture capital


### Okta Workforce Identity

**Core features**
- Enterprise-focused passwordless authentication (FastPass)
- Multiple authentication factors: WebAuthn/FIDO2, Okta Verify, Windows Hello, TouchID, FaceID
- Push notifications and biometric verification via Okta Verify app
- Magic links for email-based authentication
- Factor sequencing and step-up authentication for high-risk actions
- Adaptive MFA with risk-based challenge triggers
- Support for X.509 certificate and PIV/Smart-Card authentication
- 100% passwordless deployment (Okta internal case study)
- Scalable to large enterprise deployments
- Device credential binding and session revocation

**Differentiating features**
- Enterprise-proven at Okta's own scale (internal passwordless migration)
- FastPass: single-interaction MFA (vs. multi-step competitors)
- Wide range of factor types (certificative, biometric, app-based)
- Managed by Okta's identity team with focus on workforce use cases
- Phishing-resistant policies across internal deployments

**UX patterns**
- Factor-centric (users select preferred factor from menu)
- High-assurance single interaction (FastPass vs. multi-step MFA)
- Device binding reduces repeat challenges
- Push notification-based approval workflow

**Integration points**
- Okta API for factor management
- OIDC/OAuth 2.0 provider
- SAML 2.0 for federated identity
- Extensive directory integration (LDAP, AD, etc.)
- Event hooks for custom workflows

**Known gaps**
- Designed for workforce (large-scale internal users); less optimized for external customer identities
- Smaller developer community vs. Auth0
- No self-hosting option
- High-touch sales process for enterprises

**Licence / IP notes**
- Proprietary; managed by Okta


### Hanko

**Core features**
- Open-source passkey-first platform (Apache 2.0 / AGPL)
- Passkeys as primary method; fallback to email passcodes
- Web components for login and profile management (<hanko-auth>, <hanko-profile>)
- Self-hosting via Docker or direct deployment
- Managed Hanko Cloud option with no data dependency
- Framework-agnostic (React, Next.js, Vue, Svelte, Angular, plain HTML)
- User data export and migration between cloud and self-hosted
- No vendor lock-in due to open-source license
- Drop-in integration via HTML web components
- FIDO Alliance member and FIDO2-certified

**Differentiating features**
- True open-source with self-hosting option (no SaaS lock-in)
- Passkey-first without legacy password fallback
- Web components (vs. framework-specific UI libraries)
- Full data portability between cloud and self-hosted
- European origin (privacy-focused)

**UX patterns**
- Web component architecture (framework-agnostic)
- Passkey-first user experience
- Email code fallback for unsupported devices
- Social login optional (vs. mandatory)
- User profile self-service for account management

**Integration points**
- Runs in any HTML/framework environment
- REST API for custom integrations
- Open API specification
- Webhook system for event processing
- Open-source plugin ecosystem

**Known gaps**
- Smaller integration ecosystem vs. commercial competitors
- Limited advanced analytics
- No enterprise SSO features (SAML, SCIM) in base open-source
- Community-driven development (slower release cycle than commercial)
- Hanko Cloud lacks marketplace integrations

**Licence / IP notes**
- Apache 2.0 and AGPL dual-license; free and open-source
- Source code auditable; no hidden data collection


### Supabase Auth

**Core features**
- Open-source authentication module (MIT/Apache 2.0) integrated with Supabase BaaS
- Magic links: time-limited single-use email links
- Email OTP: six-digit codes sent via email
- SMS OTP and phone authentication
- Social login (Google, GitHub, Apple, Discord, etc.)
- Passwordless flows with optional password fallback
- Row-level security (RLS) policies attached to auth
- Built-in CAPTCHA protection
- Multi-language support (helpers for web and mobile frameworks)
- Self-hosting capability (part of Supabase open-source stack)
- SOC 2 Type II on Pro plans with 99.9% SLA

**Differentiating features**
- Integrated with Supabase PostgreSQL BaaS (auth + database in one platform)
- Row-level security policies tied to authentication context
- Self-hosting via self-hosted Supabase stack
- Simple magic link and OTP without external dependency on email service
- Built-in rate limiting and CAPTCHA for abuse prevention

**UX patterns**
- SQL-driven: RLS policies define access control
- Minimal configuration for magic links and OTP
- Email-first authentication flow
- Phone number optional for SMS delivery
- Social login as alternative path

**Integration points**
- PostgreSQL row-level security (RLS)
- OAuth 2.0/OIDC provider
- REST and GraphQL APIs
- Webhook system
- JavaScript/TypeScript SDKs (web, React Native, Flutter helpers)

**Known gaps**
- No passkey/WebAuthn support (as of 2026)
- No advanced MFA or adaptive authentication
- Limited enterprise SSO (no SAML, SCIM)
- Tightly coupled to Supabase ecosystem (difficult to use standalone)
- Smaller community vs. Auth0

**Licence / IP notes**
- MIT and Apache 2.0 dual-license (open-source)
- Self-hosting allows data residency control


### Keycloak

**Core features**
- Open-source identity and access management (Apache 2.0)
- WebAuthn/FIDO2 and passkey support with simplified registration and authentication
- Enable Passkeys switch for seamless integration
- Conditional and modal UI for passkey flows in login forms
- Flexible authentication: passkey, password, X.509 certificate, or combinations
- User federation and identity provider bridging (LDAP, Active Directory, etc.)
- Strong authentication, user management, fine-grained authorization
- SAML 2.0 and OpenID Connect (OIDC) support
- Application-initiated actions and custom flows
- Realm-level configuration
- Self-hosting via Docker, Kubernetes, or on-premises

**Differentiating features**
- Mature, enterprise-proven open-source platform
- Passkey support with minimal configuration (Enable Passkeys toggle)
- Extensive user federation and legacy system bridging
- Fine-grained authorization policies (beyond simple RBAC)
- Red Hat backing (production support available)

**UX patterns**
- Admin console for configuration (vs. UI builder)
- Flexible authentication policies with conditional UIs
- User self-service for account management
- Integration with standard protocols (OIDC, SAML)

**Integration points**
- LDAP and Active Directory user federation
- OAuth 2.0/OIDC provider and client
- SAML 2.0 identity provider
- WebAuthn4J library for passkey support
- Custom providers and SPIs for extensions
- Keycloak as OIDC client to external IdPs

**Known gaps**
- Steep learning curve (powerful but complex)
- No no-code flow builder (configuration requires deep understanding)
- Limited built-in analytics and fraud detection
- Community-driven; slower release cycle than commercial
- Requires infrastructure expertise for self-hosting at scale

**Licence / IP notes**
- Apache 2.0 (open-source)
- Self-hosting available; Red Hat commercial support optional


## Cross-Cutting Feature Themes

### Table-Stakes Features

Any passwordless authentication SDK in this space must include:

- **Passkey/WebAuthn support**: FIDO2 certification and seamless passkey registration/authentication
- **Magic link authentication**: time-limited, single-use email links with fallback OTP
- **Email and SMS OTP**: flexible one-time passcode delivery
- **Device biometric integration**: Face ID, Touch ID, Windows Hello as authenticators
- **Social and enterprise SSO**: OAuth 2.0/OIDC connectors plus SAML 2.0 for enterprise IdPs
- **Session management**: short-lived tokens, refresh rotation, device session listing, revocation
- **Drop-in UI components**: pre-built login/registration flows reducing custom work
- **Admin dashboard**: authentication metrics, drop-off analysis, user management
- **API and SDK availability**: REST API with language-specific SDKs (JavaScript, Python, Java, etc.)
- **Mobile support**: iOS and Android native SDKs or cross-platform libraries (React Native, Flutter)

### Differentiating Features

Capabilities present in some solutions offering competitive advantage:

- **No-code/low-code flow builders**: drag-and-drop authentication flows without code (Descope; absent in others)
- **Passkey-first philosophy**: treating passwords as deprecated, not a required fallback (Passage, Hanko)
- **A/B testing for authentication**: measure impact of different methods/flows (Descope)
- **Adaptive MFA with risk signals**: challenge users based on anomaly detection (Auth0, Descope, Stytch, Okta)
- **Multi-tenancy and organization management**: support for B2B use cases (Stytch, Descope, Auth0)
- **B2B SSO and SCIM provisioning**: enable enterprise customer self-service (Stytch, Auth0)
- **Progressive enrollment workflows**: nudge existing password users to passwordless without disruption (Auth0, Descope, Clerk)
- **Open-source with self-hosting**: data residency and vendor lock-in control (Hanko, Supabase, Keycloak)
- **Email infrastructure expertise**: optimize delivery reliability and reduce abuse (MojoAuth)
- **Unified multi-method API**: single interface for passkeys, magic links, OTP, social (Stytch, MojoAuth)
- **Cross-device passkey sync**: abstract platform differences (Apple, Google, Windows) (Passage, Auth0)
- **7,000+ pre-built integrations**: SIEM, analytics, fraud detection, marketing platforms (Auth0 only)

### Underserved Areas / Opportunities

Gaps that multiple solutions share, representing genuine opportunities:

- **Usage-based pricing on authenticated users**: Most platforms charge monthly active users (MAU) or fixed tiers. Platforms with bursty or seasonal traffic face high costs. Usage-based pricing aligned to login events would be attractive.
- **Self-hosted passwordless without complexity**: Hanko and Keycloak are open-source, but Keycloak is complex and Hanko is niche. A simpler, self-hosted passwordless SDK would address mid-market enterprises.
- **Passwordless-only stack**: Most solutions retain passwords as fallback. A truly passwordless-first platform (no password support at all) would differentiate.
- **AI-driven fraud detection**: Current solutions use device fingerprinting and rule-based signals. ML-based anomaly detection trained on real attack patterns would add value.
- **Unified developer experience across all platforms**: Current SDKs are fragmented (web, iOS, Android, React Native, Flutter). A unified abstraction reducing platform-specific code would appeal to cross-platform teams.
- **Advanced analytics on conversion and adoption**: Most tools show drop-off in login funnels, but lack insights into why users abandon (UX pain points, device support issues, etc.). Root-cause analytics would help optimize.
- **Compliance and audit tooling for regulated industries**: Healthcare, finance, and government need audit trails, data residency options, and policy enforcement. Few platforms deeply address compliance workflows.
- **Passwordless-specific cost modeling**: Enterprise customers struggle to predict costs when users are seasonal or bursty. Transparent per-auth pricing vs. MAU would reduce procurement friction.

### AI-Augmentation Candidates

Features currently implemented with manual or rule-based approaches but where AI could excel:

- **Smart method recommendation**: AI could infer best authentication method for user segment (new vs. returning, geographic location, device type) vs. hardcoded rules.
- **Adaptive fraud scoring**: ML models trained on real attack patterns could replace hand-tuned risk rules, improving both security and UX.
- **Personalized passwordless nudging**: AI could analyze user behavior to determine optimal time and method to suggest passwordless migration (vs. one-size-fits-all).
- **Anomaly-based account takeover detection**: Detect account abuse patterns (velocity, geo jumps, device anomalies) using unsupervised learning.
- **Proactive threat intelligence**: Feed real-time breach databases and phishing patterns into risk scoring (vs. static IP blocklists).
- **User cohort segmentation**: Automatically segment users by authentication behavior, adoption patterns, and risk profile for targeted rollout strategies.
- **Multi-factor strategy optimization**: AI could recommend optimal factor sequences (e.g., "biometric for returning users, OTP for new users in country X") based on conversion and security data.

## Legal & IP Summary

No copyright, licensing, or patent conflicts were identified in the sources reviewed. All commercial solutions are proprietary SaaS offerings with clear terms of service. Open-source solutions (Hanko, Supabase, Keycloak) use standard permissive (MIT, Apache 2.0) or copyleft (AGPL) licenses clearly documented. Auth0, Descope, and Okta claim SOC 2 Type II and/or HIPAA compliance, suitable for healthcare and regulated verticals. No evidence of active software patents encumbering core techniques (WebAuthn, passkey registration, magic links, OTP) was found; these are industry-standard protocols published by FIDO Alliance and IETF. FIDO2/WebAuthn is a published standard, and Hanko is a FIDO Alliance member. If the project plans to implement proprietary fraud detection or risk-scoring algorithms, independent patent review is recommended before finalizing implementation strategies. No material was omitted due to IP uncertainty.

## Recommended Feature Scope

Based on the analysis, here is a prioritised feature scope for a new passwordless authentication SDK:

**Must-have (MVP)**:
- Passkey/WebAuthn registration and authentication (FIDO2-certified)
- Magic link delivery via email with configurable expiration
- Email and SMS one-time passcodes (OTP)
- Device biometric support (Face ID, Touch ID, Windows Hello integration)
- Drop-in authentication UI components for web and mobile (React, iOS, Android)
- Session management with short-lived JWTs and refresh token rotation
- Admin dashboard showing authentication metrics and user management
- REST API and SDKs for web, iOS, Android
- Social login integrations (Google, GitHub, Apple, Facebook)

**Should-have (v1.1)**:
- No-code/low-code flow builder for non-technical operators
- Adaptive MFA with risk-based challenge triggers
- Progressive enrollment workflow (password → passwordless migration)
- B2B features: multi-tenancy, organization management, SSO connectors
- A/B testing for authentication methods with funnel analytics
- SAML 2.0 for enterprise identity providers
- Email infrastructure optimization (delivery reliability, abuse prevention)
- Open-source core with self-hosting option for data-residency compliance
- SCIM 2.0 provisioning for enterprise customer identity sync

**Nice-to-have (backlog)**:
- Usage-based pricing on authenticated users (vs. fixed MAU)
- Passwordless-only mode (no password support)
- AI-driven fraud detection and anomaly-based account takeover prevention
- Advanced compliance and audit tooling (for healthcare, finance, government)
- Unified cross-platform SDK abstraction (reduce platform-specific code)
- Multi-factor strategy optimization engine
- Real-time threat intelligence integration
