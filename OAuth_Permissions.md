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

## Requested Scopes

CharlyTTS requests the following YouTube OAuth scopes:


https://www.googleapis.com/auth/youtube.readonly
https://www.googleapis.com/auth/youtube.force-ssl


The application does not request:

- `https://www.googleapis.com/auth/youtube`
- `https://www.googleapis.com/auth/youtube.channel-memberships.creator`

---

## Purpose of YouTube Access

The YouTube OAuth permissions are used only for:

1. Identifying the authenticated YouTube channel.
2. Detecting whether the channel currently has an active livestream.
3. Changing the title of the streamer's own live broadcast, when the streamer asks for it.
4. Requesting an ad break on the streamer's own live broadcast, when the streamer asks for it and YouTube reports the channel as eligible.

---

## Functions Using YouTube OAuth

### `getChannelInfo()` (youtube.readonly)

Endpoint:


GET /youtube/v3/channels?part=snippet&mine=true


Purpose:

Retrieves basic information about the authenticated channel:

- Channel ID
- Channel title
- Channel handle

This information is displayed inside the CharlyTTS control panel.

---

### `getActiveStreamId()` (youtube.readonly)

Endpoint:


GET /youtube/v3/liveBroadcasts?part=id,status


Purpose:

Detects whether the authenticated channel currently has an active broadcast and retrieves the livestream identifier required for chat connection.

---

### `setTitle()` (youtube.force-ssl)

Endpoints:


GET /youtube/v3/videos?part=snippet
PUT /youtube/v3/videos?part=snippet


Purpose:

Lets the streamer change the title of their own live broadcast from inside the app (panel, chat command or voice command). The current snippet is read first and only the title is changed, so no other field is modified.

---

### `getAdEligibility()` and `startAdBreak()` (youtube.force-ssl)

Endpoints:


GET /youtube/v3/liveBroadcasts?part=monetizationDetails
POST /youtube/v3/liveBroadcasts/cuepoint


Purpose:

Lets the streamer request an ad break on their own live broadcast. The app first checks whether the broadcast is eligible for ads and only sends the request if it is. This information is used only for that check; it is not stored or shown elsewhere.

---

## YouTube Data Handling

CharlyTTS does not:

- Upload or delete videos.
- Modify YouTube content, apart from the live broadcast title changed by the streamer.
- Publish messages through the YouTube API.
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


If the streamer turns on moderation actions, CharlyTTS also requests:


moderation:ban


## Purpose

| Scope | Purpose |
|---|---|
| user:read | Identify the authenticated Kick account |
| channel:read | Retrieve channel information |
| channel:write | Allow channel title/category changes through supported commands |
| chat:write | Allow the application to send messages to Kick chat |
| moderation:ban | Optional: timeouts and bans chosen by the streamer |

Kick OAuth tokens are stored locally on the user's computer.

The token exchange uses the same secure proxy pattern used for YouTube.

---

# Twitch Authentication

CharlyTTS connects to Twitch through Twitch's standard OAuth authorization flow.

The streamer authorizes the base permissions needed to read chat and receive channel events. Permissions for optional features (for example, moderation actions) are requested only when the streamer turns those features on.

Twitch tokens are stored locally on the user's computer.

---

# Discord Integration (Optional)

Discord integration does not use an OAuth consent flow.

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

The developer-controlled server infrastructure is limited to:

- Secure OAuth token exchange through a proxy service.
- Public YouTube video and channel lookups for the song request feature, for streamers who do not use their own YouTube API key. These lookups use public data only, are not linked to any user account, and are only cached for up to 24 hours.

---

# Changes to OAuth Permissions

Any future changes to requested OAuth scopes will require updating this document to accurately describe:

- The new permissions requested.
- The functions using those permissions.
- The purpose of accessing the data.
