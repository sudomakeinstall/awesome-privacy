# Search Engines

Google collects an incredible amount of information about you--go to [https://myactivity.google.com] and see for yourself.  Luckily, Google allows you to view and delete this information if you wish.  [DuckDuckGo](https://duckduckgo.com) is a competing search engine which pledges not to collect your data.  Set DuckDuckGo to be the default search engine on all browsers (and all devices).  You may also wish to sign out of the Google Maps and YouTube apps on mobile devices.

# Use HTTPS

Web communication normally occurs over either HTTP (the Hypertext Transfer Protocol) or HTTPS (HTTP over Transport Layer Security).  HTTP communications are unencrypted, whereas HTTPS communications are encrypted.  It is generally advisable to use HTTPS anywhere it is available, *especially* when submitting sensitive information such as usernames and passwords.  [HTTPS Everywhere](https://www.eff.org/https-everywhere) is a browser plugin which attempts to force an HTTPS connection, and which can be set to block communications over HTTP entirely. 

# Browser Settings

Browsers generally have a few simple settings which can be updated to increase privacy.  Specifically:

- Enable any built-in add blockers.
- Send a ``Do Not Track'' message with all requests.
- Block third party cookies.

# Third Party Add Blockers

In addition to built-in add blockers, browser plugins have been built which block adds and tracking code.  [UBlock Origin](https://github.com/gorhill/uBlock/blob/master/README.md) and [Privacy Badger](https://www.eff.org/privacybadger) are widely used examples which can be used together or separately.

# Password Managers

To the best of your ability, all your passwords should be unique and high entropy.  That is, passwords should be long strings of complete gibberish, and should not be shared between services.  Because it is infeasible for any human to remember even *one* high entropy password (nevermind dozens), a password manager is absolutely essential.  [LastPass](https://www.lastpass.com) is a popular option with an excellent security record.  [Enpass](https://www.enpass.io) is a welcome alternative for those who prefer their passwords to be stored locally.

# Two Factor Authentication

Now that you've got complex, unique passwords for all your logins, it's time to set up two factor authentication.  Check whether the service you're using provide two factor authentication on [twofactorauth.org], and complain about it if it doesn't.  And when you *do* set up two factor authentication, make sure to use a one-time, time-based authentication token, such as with the [Google Authenticator App](https://support.google.com/accounts/answer/1066447?hl=en).  This is advantageous over SMS because (a) SMS may be unavailable if you are travelling or have poor service, and (b) because SMS is subject to its own security vulnerabilities.

# Text Messaging

If your text messages and phone calls are end-to-end encrypted, then they can't be decrypted on a central server, and won't end up in the next hacker's data dump.  [Signal Private Messenger](https://whispersystems.org) is far from the only option, but it scores well because it is easy to use, has both mobile and desktop clients, enables end-to-end encryption by default, and...is not owned by Google, Apple, or Facebook.  ;-)

# DNS Encryption

- DNSCrypt
- OpenDNS

# VPN

- Opera's VPN
Privacy Badger > Settings > General Settings > Prevent WebRTC from leaking local IP address

# Mail Clients
- Proton Mail

# IPv4 vs IPv6
- https://ipv6test.google.com
- https://www.google.com/intl/en/ipv6/faq.html

# IOT
- showdan.io

# Website Administration
- letsencrypt
- 2FA for registrar
- Dane DNS

# Disable WebRTC
- https://whoer.net/blog/article/how-to-disable-webrtc-in-various-browsers/

# Check if you are leaking your IP
- https://whoer.net
