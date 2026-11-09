# Privacy Policy

**Last updated:** November 9, 2026

## Introduction

CharlyTTS is a Windows desktop application designed for livestream creators. This Privacy Policy explains what information the application accesses, how it is used, how long it is kept, and how users can remove it.

CharlyTTS runs on the user's own computer. It is not a cloud service and does not maintain a centralized database of user accounts, chat messages, or streaming data.

---

## YouTube API Services

CharlyTTS uses YouTube API Services. By using the YouTube features of CharlyTTS, users agree to be bound by the [YouTube Terms of Service](https://www.youtube.com/t/terms).

Information obtained through YouTube API Services is also subject to the [Google Privacy Policy](https://policies.google.com/privacy).

CharlyTTS's use and transfer of information received from Google APIs adheres to the [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy), including the Limited Use requirements.

### What YouTube information CharlyTTS accesses

When the streamer connects their YouTube account:

* Basic channel information (channel ID, title and handle), to show which account is connected.
* Whether the channel has an active live broadcast, to connect to its live chat.
* The title of the streamer's own live broadcast, only when the streamer asks the app to change it.
* Whether the live broadcast is eligible for ads, only when the streamer asks the app to request an ad break.

For the optional Song Request feature, when a viewer requests a video:

* Public information about that video and its channel (such as title, duration, category, channel name and licensing flags), to decide whether it can enter the streamer's song queue.

### How this information is used and stored

* YouTube information is used only to provide the features listed above, on the streamer's own computer.
* Public video and channel information for Song Request is cached on the streamer's computer for at most 30 days and then deleted automatically.
* Song requests may use the streamer's own YouTube API key or, if the streamer has none, a server operated by the developer. That server only forwards the public video lookup, does not link it to any user account, and keeps the response for at most 24 hours.
* Song lists the streamer saves on purpose (playlists and approved songs) stay on the streamer's computer until the streamer removes them.
* YouTube information is not sold, not used for advertising, and not shared with third parties, except as described in "Third-Party Services".

### Cookies and data stored on the user's device

CharlyTTS shows YouTube's own pages inside the application: the embedded YouTube player for Song Request and the YouTube live chat page. These YouTube pages may store cookies and similar data on the user's computer, as they would in a web browser. That data is governed by the Google Privacy Policy. Signing out of YouTube inside CharlyTTS, or deleting the application's data folder, removes it from the computer.

### Revoking access

Users can revoke CharlyTTS's access to their Google account at any time from the Google security settings page: [https://myaccount.google.com/permissions](https://myaccount.google.com/permissions)

Users can also disconnect YouTube inside CharlyTTS, which deletes the locally stored access tokens.

---

## Other Information CharlyTTS Accesses

Depending on the platforms the user connects:

* Basic account information (such as channel ID, channel name, or username).
* Information required to detect active livestreams.
* Live chat messages from the user's own channel, to read them aloud, moderate them and show them in the user's overlays.
* User preferences and application settings stored locally.

The application only requests the permissions required for its features.

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

When users connect supported platforms (such as YouTube, Twitch or Kick), standard OAuth authentication is used.

Client secrets are not distributed with the desktop application.

A Cloudflare Worker is used to securely exchange authorization codes for OAuth tokens. The Worker does not store user access tokens or personal information.

OAuth tokens are stored locally on the user's own computer.

---

## Local Storage

Application settings, configuration files, OAuth tokens, logs and user preferences are stored only on the user's local device.

---

## Third-Party Services

Depending on the features enabled by the user, CharlyTTS communicates with these services:

* Google / YouTube (account connection, live chat, Song Request, embedded player)
* Twitch
* Kick
* TikTok (reading live chat)
* Discord (optional voice and notification features)
* Apple iTunes Search and Deezer (Song Request: the artist and song name are looked up in their public catalogs to warn the streamer about commercial music; no user information is sent)

* An AI moderation provider chosen by the user (only in versions that offer this optional feature, and only if the user turns it on): chat messages are sent directly from the user's computer to that provider for moderation. The developer does not proxy, inspect or store these requests.

These services are governed by their own privacy policies.

### Discord (Optional)

Discord features do not use an OAuth consent flow. The streamer manually provides their own Discord bot token, created and authorized by themselves through Discord's Developer Portal. This token is used only for the optional voice/TTS and notification features the streamer explicitly enables, and is stored locally like any other credential.

---

## Deleting Your Data

* Data stored on the user's computer can be deleted by removing the application and its data folder.
* Song Request video information is deleted automatically after 30 days.
* Google access can be revoked at any time from [https://myaccount.google.com/permissions](https://myaccount.google.com/permissions).
* The developer does not keep user data on its servers. For any question or request about data, contact the developer at the address below; requests are answered within 7 days.

---

## Data Security

CharlyTTS has been designed to minimize the exposure of sensitive credentials.

Developer OAuth client secrets are kept outside the distributed application.

Users remain responsible for protecting their own computers and local configuration files.

---

## Changes

This Privacy Policy may be updated as the application evolves. The latest version is always available at [https://charlytts.com/Privacy_Policy.html](https://charlytts.com/Privacy_Policy.html).

---

## Contact

For questions regarding this Privacy Policy, please contact the developer at:

charylbotsupport@gmail.com
