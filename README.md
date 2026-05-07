# Password-less Auth SDK

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An open-source, passkey-first authentication SDK that gives developers a single coherent API for WebAuthn, magic links, OTP, and device biometrics -- replacing passwords as the default.

Password-less Auth SDK provides the building blocks for developers to eliminate traditional username/password login in favour of passkeys (FIDO2/WebAuthn), magic links, one-time passcodes, and device biometrics. It targets product teams and engineering organisations that want to reduce credential-theft attack surface, cut password-reset support costs, and deliver a lower-friction login experience. By 2026, 45% of organisations have deployed passkeys in at least one application, with a further 27% planning adoption within two years.

---

## Why Password-less Auth SDK?

- **No credible open-source passkey-first option exists.** Hanko is the closest but lacks enterprise SSO (SAML, SCIM) in its open-source tier. Keycloak supports passkeys but carries steep operational complexity. Neither offers a simple, self-hosted passwordless SDK for mid-market teams.
- **Commercial platforms lock you in.** Auth0, Descope, Stytch, and Clerk are all proprietary SaaS with no self-hosting path, creating data-residency problems for regulated industries (healthcare, finance, government).
- **MAU pricing punishes bursty traffic.** Most incumbents charge per monthly active user regardless of login frequency. Applications with seasonal or event-driven traffic overpay significantly; usage-based pricing aligned to authentication events does not exist in the market.
- **Cross-platform passkey sync is fragmented.** Apple Keychain, Google Password Manager, and Windows Hello each handle passkey sync differently. Developers must write platform-specific code to paper over inconsistencies. No incumbent offers a unified abstraction layer.
- **Incumbents treat passwords as the default.** Most platforms retain passwords as a primary fallback. A passkey-first SDK that treats passwords as a deprecated legacy option nudges teams toward the most secure default from day one.

---

## Key Features

### Passkey and Biometric Authentication

- FIDO2/WebAuthn credential registration and authentication bound to device and origin
- Cross-device passkey sync abstraction across Apple, Google, and Windows platforms
- Device biometric integration (Face ID, Touch ID, Windows Hello) as local authenticators
- Step-up authentication for high-risk actions without full re-login

### Magic Links and One-Time Passcodes

- Time-limited, single-use magic links delivered via email with configurable expiration
- Fallback OTP for environments where link clicking is blocked
- SMS and TOTP one-time passcodes compatible with authenticator apps
- Email infrastructure optimization for delivery reliability and abuse prevention

### Drop-in UI Components and SDKs

- Pre-built, customisable login and registration screens for web and native mobile
- Platform coverage: iOS, Android, React Native, Flutter
- REST API with language-specific SDKs (JavaScript, Python, Java)
- Headless mode for teams that need full control over the user experience

### Session Management and SSO

- Short-lived JWTs with refresh-token rotation
- Device session listing and remote revocation
- OAuth 2.0/OIDC connectors for Google, Apple, GitHub, and other social providers
- SAML 2.0 for enterprise identity providers
- SCIM 2.0 provisioning for enterprise customer identity sync

### Admin Dashboard and Analytics

- Authentication method adoption rates and drop-off funnel analysis
- Failed attempt trends and anomalous login detection
- User management console with bulk operations
- A/B testing for authentication methods with conversion metrics

---

## AI-Native Advantage

Current passwordless solutions rely on hand-tuned rules for risk scoring and static IP blocklists for fraud detection. An AI-native approach replaces these with ML models trained on real attack patterns -- adaptive fraud scoring that improves both security and user experience simultaneously. AI can also drive smart method recommendation (inferring the best authentication method based on user segment, device type, and geography), personalised passwordless migration nudging (determining when and how to suggest passkey adoption), and anomaly-based account takeover detection using unsupervised learning on velocity, geolocation jumps, and device fingerprint anomalies.

---

## Tech Stack & Deployment

- **Self-hosted deployment** via Docker or Kubernetes for organisations with data-residency requirements
- **Managed cloud option** for teams that prefer not to operate infrastructure
- **Open standards**: FIDO2/WebAuthn (W3C/FIDO Alliance), OAuth 2.0, OpenID Connect, SAML 2.0, SCIM 2.0
- **Open-source core** with a permissive licence to eliminate vendor lock-in and enable auditability

---

## Market Context

The customer identity and access management (CIAM) market is dominated by Auth0/Okta (~20% mindshare), with Descope, Stytch (acquired by Twilio in November 2025), Passage by 1Password, and Clerk as significant commercial players. Incumbent pricing is typically MAU-based, with free tiers capping at low thousands of users and paid plans scaling to enterprise contracts. Primary buyers are product engineering teams at SaaS companies, platform teams at mid-market enterprises, and CTOs at regulated-industry organisations who need self-hosted data residency.

---

## Project Status

> This project is in the **research and specification phase**.
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
