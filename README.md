This awesome list is aimed at bringing us all up to date on basic, common sense practices for maintaining personal security and privacy online.  This is targeted at anyone who uses the internet and is concerned about their own online presence--not for infosec experts or people trying to secure a website.  Feel free to send a pull request if you spot any errors or omissions!

## Password Managers

To the best of your ability, all your passwords should be unique and high entropy.  That is, passwords should be long strings of complete gibberish, and should not be shared between services.  Because it is infeasible for any human to remember even *one* high entropy password (nevermind dozens), a password manager is absolutely essential.  [LastPass](https://www.lastpass.com) is a popular option with an excellent security record.  [Enpass](https://www.enpass.io) and [KeePassX](https://www.keepassx.org) are welcome alternatives for those who prefer their passwords to be stored locally.

## Two Factor Authentication

Now that you've got complex, unique passwords for all your logins, it's time to set up two factor authentication (2FA).  Check whether the service you're using provides 2FA on https://twofactorauth.org, and complain about it if it doesn't.  And when you *do* set up two factor authentication, make sure to use a one-time, time-based authentication token, such as with the [Google Authenticator App](https://support.google.com/accounts/answer/1066447?hl=en) or [Authy](https://authy.com).  This is advantageous over SMS because (a) SMS may be unavailable if you are travelling or have poor service, and (b) because SMS is subject to its own security vulnerabilities.

## Text Messaging

If your text messages and phone calls are end-to-end encrypted, then they can't be decrypted on a central server, and won't end up in the next hacker's data dump.  [Signal Private Messenger](https://whispersystems.org) is far from the only option, but it scores well because it is easy to use, has both mobile and desktop clients, enables end-to-end encryption by default, and...is not owned by Google, Apple, or Facebook.  ;-)  Of course, if the device itself is compromised, end-to-end encryption won't help; but it will work for most people, most of the time.

## Search Engines

Google collects an incredible amount of information about you--go to https://myactivity.google.com and see for yourself.  Luckily, Google allows you to view and delete this information if you wish.  [DuckDuckGo](https://duckduckgo.com) is a competing search engine which pledges not to collect your data.  Set DuckDuckGo to be the default search engine on all browsers (and all devices).  You may also wish to sign out of the Google Maps and YouTube apps on mobile devices.

## Use HTTPS

Web communication normally occurs over either HTTP (the Hypertext Transfer Protocol) or HTTPS (HTTP over Transport Layer Security).  HTTP communications are unencrypted, whereas HTTPS communications are encrypted.  It is generally advisable to use HTTPS anywhere it is available, *especially* when submitting sensitive information such as usernames and passwords.  [HTTPS Everywhere](https://www.eff.org/https-everywhere) is a browser plugin which attempts to force an HTTPS connection, and which can be set to block communications over HTTP entirely. 

## Browser Settings

Browsers generally have a few simple settings which can be updated to increase privacy.  Specifically:

- Enable any built-in add blockers.
- Send a "Do Not Track" message with all requests.
- Block third party cookies.

## Third Party Add Blockers

In addition to built-in add blockers, browser plugins have been built which block adds and tracking code.  [UBlock Origin](https://github.com/gorhill/uBlock/blob/master/README.md) and [Privacy Badger](https://www.eff.org/privacybadger) are widely used examples which can be used together or separately.

## Domain Name System (DNS) Encryption

DNS is the system by which a URL such as www.google.com is translated into an IP address such as 172.217.4.142.  Unfortunately, this protocol does not encrypt or authenticate the transaction, leaving us open to a number of security vulnerabilities.  [DNSCrypt](https://www.dnscrypt.org) solves this problem.

## Virtual Private Network (VPN)

Since the US congress has voted to [relax regulations](https://motherboard.vice.com/en_us/article/senate-republicans-vote-to-allow-isps-to-sell-your-private-data) preventing internet service providers (ISPs) from selling users' browsing histories, VPNs have become more important.  Choosing a VPN is a [complicated topic](https://arstechnica.com/security/2016/06/aiming-for-anonymity-ars-assesses-the-state-of-vpns-in-2016/), and may require a paid service depending on your circumstances.  A detailed comparison of the many available options can be found [here](https://thatoneprivacysite.net/vpn-section/).  But if you're just a casual user seeking to stick it to Comcast, check out [Opera](https://www.opera.com).  This lesser-known browser (a competetor to Firefox, Chrome, etc) has a built-in VPN called SurfEasy.  Currently, SurfEasy offers unlimited data use and pledges not to keep logs.  (There's got to be a catch somewhere, but I haven't found it yet.)

Although a VPN provides you with an IP address distinct from your own, it is likely that you will initially be leaking your true IP address due a protocol called WebRTC which is built into most browsers.  Luckily, you can prevent this using Privacy Badger by going to Settings, then General Settings, and checking "Prevent WebRTC from leaking local IP address," or by installing the WebRTC Network Limiter browser extension.  The success of these techniques may differ depending on the browser you are using, so make sure to check that your ip is hidden at https://ipleak.net.

It is important to recognize that by using a secure VPN you are maintaining privacy from your ISP, but still must trust your VPN provider.  An intriguing solution is to [host your own personal VPN](https://arstechnica.com/gadgets/2017/05/how-to-build-your-own-vpn-if-youre-rightfully-wary-of-commercial-options/), trading some technical effort and a small monthly fee for piece of mind.

## Audit Your Security

There are a large number of websites where you can audit your security to see what information you might be leaking.  Here are just a few:

- https://panopticlick.eff.org
- https://www.dnsleaktest.com
- https://www.ipleak.net
- https://browserleaks.com
- https://whoer.net

## Podcasts!

If you really want to ensure that you never get another good night's sleep, there are a number of excellent podcasts out there which will alert you to the latest and greatest cyber threats to our fragile way of life.

- [Security Now with Steve Gibson](https://www.grc.com/securitynow.htm)
- [Risky.Biz](https://risky.biz/netcasts/risky-business/)
- [The CyberWire](https://thecyberwire.com)
