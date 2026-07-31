# CharlyTTS

**CharlyTTS** is a Windows desktop application designed for livestream creators. It connects to supported streaming platforms, reads live chat messages, and provides text-to-speech, moderation, overlays, and interactive stream tools.

The application runs locally on the streamer's computer. User credentials and OAuth tokens are stored only on the user's own device.

---

## Main Features

* Text-to-Speech (TTS) for live chat.
* AI-assisted chat moderation (using the user's own API key).
* Custom overlay system for OBS.
* Interactive chat features and mini-games.
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

The application requests only the following Google OAuth scope:

`https://www.googleapis.com/auth/youtube.readonly`

This permission is used only to:

* Identify the authenticated YouTube channel.
* Detect whether the channel currently has an active livestream.

The application **does not**:

* Upload or modify YouTube content.
* Publish chat messages through the YouTube API.
* Access monetization information.
* Access membership information.

Additional technical details are available in the OAuth documentation.

---

## Documentation

* [OAuth Permissions](OAuth_Permissions.md)
* [Privacy Policy](Privacy_Policy.MD)
* [Term_of_Service](Terms_of_Service.MD)

---

## Supported Platform

* Windows (Electron)

---

## Contact

For questions about this application, its OAuth permissions, or its Privacy Policy, contact the developer at:

**charylbotlabs@gmail.com**

<!-- Reemplaza la línea de arriba por el email/contacto real antes de subir. -->
