This awesome list is aimed at bringing us all up to date on basic, common sense practices for maintaining personal security and privacy online.  This is targeted at anyone who uses the internet and is concerned about their own online presence--not for infosec experts or people trying to secure a website.  Feel free to send a pull request if you spot any errors or omissions!

## Password Managers

To the best of your ability, all your passwords should be unique and high entropy.  That is, passwords should be long strings of complete gibberish, and should not be shared between services.  Because it is infeasible for any human to remember even *one* high entropy password (nevermind dozens), a password manager is absolutely essential.  [LastPass](https://www.lastpass.com) is a popular option with an excellent security record.  [Enpass](https://www.enpass.io) and [KeePassX](https://www.keepassx.org) are welcome alternatives for those who prefer their passwords to be stored locally.

## Generate Strong (Random) Passwords

Now that you're using a password manager, the length and complexity of the passwords you use are no longer limited by what you can easily remember.  The best passwords are both long and completely random.  There are plenty of resources you can use to generate these.  For example, the [Gibson Research Corporation](https://www.grc.com/passwords.htm) has a nice page for generating high-quality passwords; an alternative from the terminal is to use the commandline utility `apg`:

```
$ apg -n 1 -m 64 -x 64 -a 1
```

## Two Factor Authentication

Now that you've got complex, unique passwords for all your logins, it's time to set up two factor authentication (2FA).  The idea behind 2FA is that two pieces of information must be supplied to authenticate an account--usually something you know (a password) and something you have (a device).  Security is increased because both these things need to be compromised for someone to access your account.

### Time-based One Time Passwords (TOTP)

Usually, the "something-you-have" device is a cell phone.  To confirm that you have control of this device, most services will offer to either (a) send you an SMS text message with a code, or (b) use an authentication app.  SMS text is generally considered to be inferior because (a) it relies on your having cell service (won't work when traveling or when out of reach of a cell tower), (b) you could be charged, and (c) SMS is [notoriously unsecure](https://www.theguardian.com/technology/2016/apr/19/ss7-hack-explained-mobile-phone-vulnerability-snooping-texts-calls).  A time-based authenticator app, such as with the [Google Authenticator App](https://support.google.com/accounts/answer/1066447?hl=en) or [Authy](https://authy.com), will use the current time along with a QR code scanned once during setup to generate a code which changes frequently.  The service you'd like to log into also knows the QR code and the current time, and so can validate the code.  Because the code is generated on the device rather than being transmitted, cannot be intercepted.

A note of caution: if you set up 2FA on your mobile device and then drop said mobile device in the toilet, you'll be in a bit of a bind.  To protect against this, most services allow you to download a small number (usually 10 to 20) of "recovery codes."  It is a good idea to keep these, but _be very careful how you store them_ (i.e., protect them as you would your passwords).  I'd recommend putting them in your password manager.  It might also be a good idea to store the QR codes themselves in your password manager as well, which will greatly ease the transition when you get a new device.

### Dedicated Hardware

You may also consider getting a dedicated hardware device, such as a [YubiKey](https://www.yubico.com/).  The benefit is that an attacker can't bypass 2FA by taking control of your phone.  The drawbacks are that fewer services support it, it's not free, and it's another thing to keep on your (physical) keychain.

So check whether the service you're using provides 2FA on https://twofactorauth.org, and complain about it if it doesn't.  And when you *do* set up two factor authentication, make sure to use an authenticator app instead of SMS text if available.

## Text Messaging

If your text messages and phone calls are end-to-end encrypted, then they can't be decrypted on a central server, and won't end up in the next hacker's data dump.  [Signal Private Messenger](https://whispersystems.org) is far from the only option, but it scores well because it is easy to use, has both mobile and desktop clients, enables end-to-end encryption by default, and...is not owned by Google, Apple, or Facebook.  ;-)  Of course, if the device itself is compromised, end-to-end encryption won't help; but it will work for most people, most of the time.

## Browser Settings

Browsers generally have a few simple settings which can be updated to increase privacy.  Specifically:

- Enable any built-in ad blockers.
- Send a "Do Not Track" message with all requests.
- Block third party cookies.
- Disable WebRTC (which can leak IP addresses, even when using a VPN)

You can lock down your browser a bit further using third party extensions.

### HTTPS Everywhere

Web communication normally occurs over either HTTP (the Hypertext Transfer Protocol) or HTTPS (HTTP over Transport Layer Security).  HTTP communications are unencrypted, whereas HTTPS communications are encrypted.  It is generally advisable to use HTTPS anywhere it is available, *especially* when submitting sensitive information such as usernames and passwords.  [HTTPS Everywhere](https://www.eff.org/https-everywhere) is a browser plugin which attempts to force an HTTPS connection, and which can be set to block communications over HTTP entirely.  I would recommend enabling the "Block all unencrypted requests" option, which can prevent you from accidentally using an HTTP connection without your knowledge.  If HTTPS Everywhere prevents a page from loading, you can then make an informed decision whether to go somewhere else, or to temporarily disable the plugin (which is very easy).

### Third Party Ad Blockers

In addition to built-in ad blockers, browser plugins have been built which block ads and tracking code.
[uBlock Origin](https://github.com/gorhill/uBlock/blob/master/README.md) and [Privacy Badger](https://www.eff.org/privacybadger) are widely used examples which can be used together or separately.
Although you've already disabled WebRTC in the browser (haven't you?), I'd recommend asking both UBlock Origin and Privacy Badger to prevent WebRTC from leaking local IP addresses (redundancy is generally a good thing).
I'd also recommend checking out [Ghostery](https://www.ghostery.com) and (uBlock Origin Extra](https://chrome.google.com/webstore/detail/ublock-origin-extra/pgdnlhfefecpicbbihgmbmffkjpaplco), which will extend the ad- and tracker-blocking utility.
One last point: by default (in all browsers I've used), these extensions are disabled if you open up a private browsing tab.
This makes excellent sense as a default--extensions have unrestricted access to your data, so opening up a supposedly "private" tab and giving all your extensions free run over it would be unintuitive and a violation of trust.
However, in the case of extensions which *enhance* your privacy rather than *degrade* it, I would suggest enabling them in private mode (which you can do in your browser's settings).

## Search Engines

Google collects an incredible amount of information about you--go to https://myactivity.google.com and https://passwords.google.com and see for yourself.  Luckily, Google allows you to view and delete this information if you wish.  [DuckDuckGo](https://duckduckgo.com) is a competing search engine which pledges not to collect your data.  Set DuckDuckGo to be the default search engine on all browsers (and all devices).  You may also wish to sign out of the Google Maps and YouTube apps on mobile devices.

## Use a Firewall

A `firewall` is a program which monitors the incoming and outgoing traffic on your network, and blocks requests based on rules set during its configuration.  Properly configured, a firewall can protect against some (but not all) attempts to remotely access your computer.

- [Ubuntu](https://wiki.ubuntu.com/UncomplicatedFirewall)
- [OS X](https://support.apple.com/en-us/HT201642)
- [Windows](https://support.microsoft.com/en-us/instantanswers/c9955ad9-1239-4cb2-988c-982f851617ed/turn-windows-firewall-on-or-off)

## Google - Privacy and Security

Google collects an enormous amount of data from us, but also provides an excellent interface for auditing and adjusting that tracking.  The launching point for all this is https://myaccount.google.com, which has a number of useful links, including:

- https://myactivity.google.com/myactivity : Audit your data, and remove anything you prefer wasn't there.
- https://myaccount.google.com/secureaccount : Do a security checkup.
- https://myaccount.google.com/privacycheckup : Do a privacy checkup.

Google also has a browser add-on which allows you to opt-out of Google Analytics.

- https://tools.google.com/dlpage/gaoptout

## Facebook - Privacy and Security

Since your data is more integral to the experience of Facebook, it is generally not possible to delete your data without also deleting your account.  However, Facebook *does* allow you to audit your data and perform privacy and security checkups, similar to Google.  Here are a few useful links:

- https://www.facebook.com/help/1701730696756992/ : Audit your data.
- https://www.facebook.com/help/securitycheckup : Perform a security checkup.
- https://www.facebook.com/settings?tab=privacy : Check your privacy settings.

## Domain Name System (DNS) Encryption

DNS is the system by which a URL (such as www.google.com) is translated into an IP address (such as 172.217.4.142).
Unfortunately, this protocol does not encrypt or authenticate the transaction, leaving us open to a number of security and privacy vulnerabilities.
A system called DNS over HTTPS (DoH) has been developed to encrypt DNS requests, but this system requires that both the client (your computer) and the DNS server support this protocol.
Until recently, this has been a bit tricky to set up on the client side, and there haven't been many good options as far as DNS servers which support the protocol.
Luckily, Cloudflare has released a DNS server [1.1.1.1](https://1.1.1.1) for free which supports DoH, and is faster than many competing DNS servers.
Start off by configuring your phones, computers, and routers to use [Cloudflares DNS](https://1.1.1.1).
Cloudflare has made the configuration of mobile devices to use DoH insanely easy using their [mobile apps](https://1.1.1.1).
Configuration on the computer is slightly more complicated, but much less complicated than it used to be using Cloudflare's [proxy](https://developers.cloudflare.com/1.1.1.1/dns-over-https/cloudflared-proxy/).

## Virtual Private Network (VPN)

Since the US congress has voted to [relax regulations](https://motherboard.vice.com/en_us/article/senate-republicans-vote-to-allow-isps-to-sell-your-private-data) preventing internet service providers (ISPs) from selling users' browsing histories, VPNs have become more important.  Choosing a VPN is a [complicated topic](https://arstechnica.com/security/2016/06/aiming-for-anonymity-ars-assesses-the-state-of-vpns-in-2016/), and may require a paid service depending on your circumstances.  A detailed comparison of the many available options can be found [here](https://thatoneprivacysite.net/vpn-section/), and a discussion on choosing a good VPN can be found [here](https://ssd.eff.org/en/module/choosing-vpn-thats-right-you).  But if you're just a casual user seeking to stick it to Comcast, check out [Opera](https://www.opera.com).  This lesser-known browser (a competetor to Firefox, Chrome, etc) has a built-in VPN called SurfEasy.  Currently, SurfEasy offers unlimited data use and pledges not to keep logs.  (There's got to be a catch somewhere, but I haven't found it yet.)

Although a VPN provides you with an IP address distinct from your own, it is likely that you will initially be leaking your true IP address due a protocol called WebRTC which is built into most browsers.  Luckily, you can prevent this using Privacy Badger by going to Settings, then General Settings, and checking "Prevent WebRTC from leaking local IP address," or by installing the WebRTC Network Limiter browser extension.  The success of these techniques may differ depending on the browser you are using, so make sure to check that your ip is hidden at https://ipleak.net.

It is important to recognize that by using a secure VPN you are maintaining privacy from your ISP, but still must trust your VPN provider.  An intriguing solution is to [host your own personal VPN](https://arstechnica.com/gadgets/2017/05/how-to-build-your-own-vpn-if-youre-rightfully-wary-of-commercial-options/), trading some technical effort and a small monthly fee for piece of mind.

## Credit Card Security

- [privacy.com](https://privacy.com/) allows you to create "burner" credit cards which can have hard limits, be single-service, or even single-use.

## Configuring Your Wireless Network

Securing a home network is a complicated task, and is for the most part beyond the scope of this document.  However, here are a few tips:

- Change the default SSID (the name of your Wifi network, which gets broadcast).  This doesn't help security much, but c'mon--don't be a n00b.
- Change the default password.  This _does_ help the security.  Many consumer routers use weak default credentials, which can be built into malicious tools which scan available networks attempting to log in.
- Enable a firewall.
- Update your router's firmware.  If you haven't done this in a while (or ever), there's a very good chance that your router has a known, unpatched security vulnerability.
- Disable universal plug-and-play (UPnP).
- Segment your network.  I'd recommend having one network for your home computers, laptops, etc., one network for any internet connected appliances, and one for guests.  By putting your personal laptop on a separate network from, say, your [internet connected flower pot](https://www.amazon.com/Parrot-Pot-Smart-Connected-Flower/dp/B01KV0JCI4), you prevent someone from gaining control over said flower pot (pwning, in the modern parlance), and moving laterally to gain control over your computer.  If your router only allows you to have two network segments, consider putting any internet-of-things on your guest network (or, better yet, burning them in a fire).

## Audit Your Security

There are a large number of websites where you can audit your security to see what information you might be leaking, and if any devices are visible on your network.  Here are just a few:

- https://panopticlick.eff.org
- https://www.dnsleaktest.com
- https://www.ipleak.net
- https://browserleaks.com
- https://whoer.net
- https://iotscanner.bullguard.com/

## Podcasts!

If you really want to ensure that you never get another good night's sleep, there are a number of excellent podcasts out there which will alert you to the latest and greatest cyber threats to our fragile way of life.

- [Security Now with Steve Gibson](https://www.grc.com/securitynow.htm)
- [Risky.Biz](https://risky.biz/netcasts/risky-business/)
- [The CyberWire](https://thecyberwire.com)
- [Troy Hunt](https://itunes.apple.com/au/podcast/troy-hunts-weekly-update-podcast/id1176454699)
- [Smashing Security](https://www.smashingsecurity.com/)
- [Darknet Diaries](https://darknetdiaries.com)
