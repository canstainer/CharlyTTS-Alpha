# OAuth Permissions and Data Handling

> CharlyTTS's use and transfer of information received from Google APIs adheres to the [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy), including the Limited Use requirements.

This document describes the OAuth permissions requested by CharlyTTS, the functions that use them, and how user data is handled.

This document is intended for technical review and platform verification.

---

# Application Overview

CharlyTTS is a Windows desktop application (Electron) designed for livestream creators.

The application runs locally on the streamer's own computer. It connects to streaming platforms, reads live chat messages, converts messages to speech (TTS), and provides moderation, overlays, and interactive stream tools.

CharlyTTS does not operate as a cloud service and does not maintain a centralized database of user accounts, OAuth tokens, or livestream data.

---

# YouTube OAuth

## Requested Scope

CharlyTTS requests only the following YouTube OAuth scope:


https://www.googleapis.com/auth/youtube.readonly


No write permissions are requested.

The application does not request:

- `https://www.googleapis.com/auth/youtube`
- `https://www.googleapis.com/auth/youtube.force-ssl`
- `https://www.googleapis.com/auth/youtube.channel-memberships.creator`

---

## Purpose of YouTube Access

The YouTube OAuth permission is used only for:

1. Identifying the authenticated YouTube channel.
2. Detecting whether the channel currently has an active livestream.

---

## Functions Using YouTube OAuth

### `getChannelInfo()`

Endpoint:


GET /youtube/v3/channels?part=snippet&mine=true


Purpose:

Retrieves basic information about the authenticated channel:

- Channel ID
- Channel title
- Channel handle

This information is displayed inside the CharlyTTS control panel.

---

### `getActiveStreamId()`

Endpoint:


GET /youtube/v3/liveBroadcasts?part=id,status


Purpose:

Detects whether the authenticated channel currently has an active broadcast and retrieves the livestream identifier required for chat connection.

---

## YouTube Data Handling

CharlyTTS does not:

- Upload videos.
- Modify YouTube content.
- Publish messages through the YouTube API.
- Access monetization information.
- Access channel membership information.

YouTube live chat is not read through the YouTube Data API.

Chat messages are accessed through an embedded YouTube chat interface inside the desktop application.

---

# YouTube Authentication Flow

CharlyTTS uses the standard OAuth 2.0 Authorization Code Flow.

The application client secret is not distributed inside the desktop application.

The authorization code exchange is handled through a Cloudflare Worker proxy.

The proxy:

- Receives authorization code exchange requests.
- Injects the protected client secret.
- Forwards requests to Google's OAuth token endpoint.

The proxy does not store:

- Access tokens.
- Refresh tokens.
- User information.

---

# Token Storage

OAuth tokens are stored only locally on the streamer's own computer.

Stored information includes:

- Access tokens.
- Refresh tokens.
- Application configuration.

CharlyTTS does not upload or store user OAuth tokens on developer-controlled servers.

---

# Revoking Access

Users can revoke access at any time through their Google Account permissions:

https://myaccount.google.com/permissions

Users can also disconnect YouTube directly inside CharlyTTS, which removes the locally stored authentication data.

---

# Kick OAuth

## Requested Scopes

CharlyTTS requests:


user:read
channel:read
channel:write
chat:write


## Purpose

| Scope | Purpose |
|---|---|
| user:read | Identify the authenticated Kick account |
| channel:read | Retrieve channel information |
| channel:write | Allow channel title/category changes through supported commands |
| chat:write | Allow the application to send messages to Kick chat |

Kick OAuth tokens are stored locally on the user's computer.

The token exchange uses the same secure proxy pattern used for YouTube.

---

# Twitch Authentication

CharlyTTS does not implement its own Twitch OAuth login flow.

The streamer provides their own Twitch authentication token.

That token is used for:

- Reading Twitch chat.
- EventSub integrations.

The permissions depend on the scopes authorized by the streamer when creating their Twitch token.

CharlyTTS does not manage Twitch OAuth credentials.

---

# Discord Integration (Optional)

Discord integration does not use an OAuth consent flow either.

The streamer manually provides their own Discord bot token, generated and authorized by themselves through Discord's Developer Portal.

This token is used only for optional features (voice/TTS and notification features) that the streamer explicitly enables.

CharlyTTS does not manage Discord OAuth credentials.

---

# General Data Handling Summary

CharlyTTS follows these principles:

- Local desktop application.
- No centralized user database.
- No developer-controlled storage of OAuth tokens.
- No selling or sharing of user information.
- Credentials remain on the user's own computer.

The developer-controlled server infrastructure is limited to secure OAuth token exchange through a proxy service and does not store user data.

---

# Changes to OAuth Permissions

Any future changes to requested OAuth scopes will require updating this document to accurately describe:

- The new permissions requested.
- The functions using those permissions.
- The purpose of accessing the data.
