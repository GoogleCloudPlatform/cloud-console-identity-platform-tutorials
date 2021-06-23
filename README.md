# IAP External Identities Support with Identity Platform

[Cloud Identity-Aware Proxy (Cloud IAP)](https://cloud.google.com/iap/)
controls access to your cloud applications and VMs running on Google Cloud Platform (GCP).
Cloud IAP verifies user identity and the context of the request to determine if a user
should be allowed to access an application or a VM.

[Google Cloud's Identity Platform (GCIP)]((https://cloud.google.com/identity-platform/))
aims to provide Developers with Google-grade Authentication and Security for their
applications, services, APIs, or anything else that requires identity and authentication.

By default, IAP uses Google identities and Cloud IAM. External identities can be used
with IAP by leveraging Identity Platform. This allows the end users to do authentication
using any identity and identity provider that GCIP supports. This means that developers
will be able to use IdPs that are supported by GCIP (SAML, OIDC, social etc)
to authenticate users.

To use
[external identities with IAP](https://cloud.google.com/iap/docs/external-identities),
your app needs a page for authenticating users. IAP will redirect any unauthenticated
requests to this page.

`gcip-iap` NPM module implements the protocol used to integrate
GCIP (Google Cloud's Identity Platform) for authenticating external identities
with IAP (Identity Aware Proxy).

## Table of Contents

1. [Overview](#overview)

## Overview

In order to use
[external identities with IAP](https://cloud.google.com/iap/docs/external-identities),
an authentication page needs to be hosted to handle authentication, tenant
selection, token refreshes, sign-out and all authentication related operations.
This page can be hosted anywhere and the same page can be shared for multiple
IAP resources or GCP projects.

The `gcip-iap` NPM module is provided to abstract the underlying communication
between GCIP and IAP on that authentication page. This will expose callbacks
for UI and authentication related logic.
You will be able to build your own authentication UI on top of this via
these callbacks using the GCIP JS library. You can also use the pre-built
[FirebaseUI](https://github.com/firebase/firebaseui-web)
library as your authentication UI.

This will allow you to use all GCIP supported external providers such as:
- Email/password
- OAuth based providers (Google, Facebook, Twitter, GitHub, Microsoft, Apple,
  LinkedIn, etc.)
- SAML based identity providers
- OIDC based identity providers
- Phone number authentication (not supported for multi-tenancy)
- Custom authentication (not supported for multi-tenancy)
- Anonymous sign-in (not supported for multi-tenancy)

Learn more on how to
[create an authentication UI with FirebaseUI](### Create an Authentication UI with FirebaseUI)
or
[create your own custom authentication UI](### Create your own Custom Authentication UI).
