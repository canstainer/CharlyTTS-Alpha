# Privacy Policy

**Last updated:** July 30, 2026

## Introduction

CharlyTTS is a Windows desktop application designed for livestream creators. This Privacy Policy explains what information the application accesses, how it is used, and how it is protected.

CharlyTTS is designed to operate primarily on the user's local computer. It is not a cloud service and does not maintain a centralized database of user accounts or streaming data.

---

## Information We Access

Depending on the streaming platform the user connects, CharlyTTS may access:

* Basic account information (such as channel ID, channel name, or username).
* Information required to detect active livestreams.
* Live chat messages from the user's own channel.
* User preferences and application settings stored locally.

The application only requests the minimum permissions required for its functionality.

---

## Information We Do Not Collect

CharlyTTS does not:

* Sell personal information.
* Build advertising profiles.
* Share user information with third parties for marketing purposes.
* Store copies of livestream chats on developer-controlled servers.
* Store OAuth access tokens on developer-controlled servers.

---

## OAuth Authentication

When users connect supported platforms (such as YouTube or Kick), OAuth authentication is used.

Client secrets are not distributed with the desktop application.

A Cloudflare Worker is used only to securely exchange authorization codes for OAuth tokens. The Worker does not permanently store user access tokens or personal information.

OAuth tokens are stored locally on the user's own computer.

---

## Local Storage

Application settings, configuration files, OAuth tokens, and user preferences are stored only on the user's local device.

Removing the application or deleting its configuration files removes this locally stored information.

---

## Third-Party Services

Depending on the features enabled by the user, CharlyTTS may communicate directly with third-party services, including:

* Google (YouTube OAuth)
* Twitch
* Kick
* OpenRouter (if the user enables AI moderation)
* Discord (optional features)

These services are governed by their own privacy policies.

---

## AI Features

Some optional features use external AI providers.

When enabled by the user, chat messages may be sent directly to the AI provider selected by the user for moderation purposes.

The developer does not proxy, inspect, or permanently store these requests.

---

## Data Security

CharlyTTS has been designed to minimize the exposure of sensitive credentials.

Developer OAuth client secrets are kept outside the distributed application.

Users remain responsible for protecting their own computers and local configuration files.

---

## Revoking Access

Users may revoke OAuth permissions at any time through the corresponding platform's account settings (for example, Google Account Permissions).

Users may also disconnect supported platforms directly from within CharlyTTS.

---

## Changes

This Privacy Policy may be updated as the application evolves.

The latest version will always be available from the project's official website.

---

## Contact

For questions regarding this Privacy Policy, please contact the developer using the contact information published on the official project website.
