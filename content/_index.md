---
draft: false
title: 'Truster'
---

<div style="text-align: center; margin: 2rem 0;">
  <img class="truster-wordmark truster-wordmark-light" src="/truster-logo.svg" alt="Truster" />
  <img class="truster-wordmark truster-wordmark-dark" src="/truster-logo-dark.svg" alt="Truster" />
</div>

## What is Truster?

Truster is a small, self-hosted OIDC provider for authenticating users and
services to your applications or Kubernetes clusters.

People sign in with an existing Google, GitHub, or compatible OAuth2/OIDC
account, or with a one-time code sent by email. Truster turns that login
into a consistent email identity and the groups you configure, without storing
user passwords.

Services can exchange trusted external OIDC tokens for scoped Truster identities
and groups instead of using static credentials.

## Why Truster?

- **Use accounts people already have.** Connect one or more Google, GitHub, or
  generic OAuth2/OIDC providers, or offer passwordless email-code sign-in.
- **Keep identity policy reviewable.** Define clients and email-to-group mappings
  in JSONC configuration, or read them from PostgreSQL when policy needs to be
  managed dynamically.
- **Start small.** Run one binary with embedded SQLite, then use PostgreSQL for
  shared protocol state when a deployment needs multiple replicas.
- **Integrate with Kubernetes or your app.** Issue normalized email and group
  claims for Kubernetes RBAC, or use Truster as the authorization server for
  a browser, server, or CLI application.
- **Authenticate services without static credentials.** Exchange OIDC tokens
  from GitHub Actions, Buildkite, or another trusted issuer after validating
  explicit claim policies, then map the service identity to scoped groups.
- **Use secure flows.** Interactive clients use Authorization Code with PKCE;
  authorization codes are opaque, short-lived, and single-use, and tokens are
  signed with asymmetric keys.
- **Deploy where it fits.** Use the official OpenTofu/Terraform modules for AWS
  or Google Cloud, or the official container image and Helm chart for Kubernetes.

Truster authenticates users and services and issues identity claims. Your
application or Kubernetes RBAC remains responsible for deciding what that
identity may do.

## Is it a good fit?

Choose Truster when you want a small login service, email addresses are
appropriate identities for your users, and your access policy can be expressed
as email-to-group mappings. It is especially useful for replacing shared or
long-lived Kubernetes credentials with browser-based login and short-lived
tokens.

Choose a broader identity platform if you need local passwords, LDAP, SAML,
account lifecycle management, or dynamic synchronization of upstream groups. Read more in 
[Why Truster?](/docs/why-truster/)

## Quick Start

Try the complete email-code sign-in flow locally in a few minutes, no cloud
account or domain required:

1. Start Mailpit to capture the demo email.
2. Run `go run ./cmd/truster serve --demo` from the Truster repository.
3. Start a login with kubelogin and copy the code from Mailpit into your browser.

The [Getting Started guide](/docs/getting-started/) has the commands and then
walks you through choosing a persistent local, AWS, or Google Cloud deployment.
You can also go directly to the [Kubernetes and Helm deployment
guide](/docs/deploy/kubernetes/).

[Get Started →](/docs/getting-started/) · [Read the Documentation →](/docs/)
