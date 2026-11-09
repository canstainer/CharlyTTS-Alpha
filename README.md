---
title: CharlyTTS
permalink: /
---

# CharlyTTS

**CharlyTTS** is a Windows desktop application designed for livestream creators. It connects to supported streaming platforms, reads live chat messages, and provides text-to-speech, moderation, overlays, and interactive stream tools.

The application runs locally on the streamer's computer. User credentials and OAuth tokens are stored only on the user's own device.

---

## Main Features

* Text-to-Speech (TTS) for live chat.
* AI-assisted chat moderation that runs on the user's computer.
* Custom overlay system for OBS.
* Interactive chat features and mini-games.
* Song requests played in the official embedded YouTube player.
* Multi-platform support.

Supported platforms:

* YouTube
* Twitch
* Kick

---

## Security

CharlyTTS has been designed to minimize the exposure of sensitive credentials.

* OAuth tokens are stored locally on the user's computer.
* Client secrets are **not** distributed inside the desktop application.
* OAuth token exchanges are handled through a Cloudflare Worker acting as a secure proxy.
* The application does not operate as a cloud service and does not maintain a centralized database of user accounts or chat data.

---

## YouTube OAuth

The application requests the following Google OAuth scopes:

* `https://www.googleapis.com/auth/youtube.readonly`
* `https://www.googleapis.com/auth/youtube.force-ssl`

These permissions are used only to:

* Identify the authenticated YouTube channel.
* Detect whether the channel currently has an active livestream.
* Let the streamer change the title of their own live broadcast from inside the app.
* Let the streamer request an ad break on their own live broadcast, only when YouTube reports the channel as eligible.

The application **does not**:

* Upload, delete or otherwise modify YouTube videos, apart from the live broadcast title changed by the streamer.
* Publish chat messages through the YouTube API.
* Access membership information.

Additional technical details are available in the OAuth documentation.

---

## Documentation

* [OAuth Permissions](OAuth_Permissions.md)
* [Privacy Policy](Privacy_Policy.MD)
* [Terms of Service](Terms_of_Service.MD)

---

## Supported Platform

* Windows (Electron)

---

## Contact

For questions about this application, its OAuth permissions, or its Privacy Policy, contact the developer at:

**charylbotsupport@gmail.com**
