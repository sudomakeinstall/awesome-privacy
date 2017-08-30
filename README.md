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

Usually, the "something-you-have" device is a cell phone.  To confirm that you have control of this device, most services will offer to either (a) send you an SMS text message with a code, or (b) use an authentication app.  SMS text is generally considered to be inferior because (a) it relies on your having cell service (won't work when traveling or when out of reach of a cell tower), (b) you could be charged, and (c) SMS is [notoriously unsecure](https://www.theguardian.com/technology/2016/apr/19/ss7-hack-explained-mobile-phone-vulnerability-snooping-texts-calls).  A time-based authenticator app, such as with the [Google Authenticator App](https://support.google.com/accounts/answer/1066447?hl=en) or [Authy](https://authy.com), will use the current time along with a QR code scanned once during setup to generate a code which changes frequently.  The service you'd like to log into also knows the QR code and the current time, and so can validate the code.  Because the code is generated on the device rather than being transmitted, cannot be intercepted.

So check whether the service you're using provides 2FA on https://twofactorauth.org, and complain about it if it doesn't.  And when you *do* set up two factor authentication, make sure to use an authenticator app instead of SMS text if available.

## Text Messaging

If your text messages and phone calls are end-to-end encrypted, then they can't be decrypted on a central server, and won't end up in the next hacker's data dump.  [Signal Private Messenger](https://whispersystems.org) is far from the only option, but it scores well because it is easy to use, has both mobile and desktop clients, enables end-to-end encryption by default, and...is not owned by Google, Apple, or Facebook.  ;-)  Of course, if the device itself is compromised, end-to-end encryption won't help; but it will work for most people, most of the time.

## Search Engines

Google collects an incredible amount of information about you--go to https://myactivity.google.com and see for yourself.  Luckily, Google allows you to view and delete this information if you wish.  [DuckDuckGo](https://duckduckgo.com) is a competing search engine which pledges not to collect your data.  Set DuckDuckGo to be the default search engine on all browsers (and all devices).  You may also wish to sign out of the Google Maps and YouTube apps on mobile devices.

## Use HTTPS

Web communication normally occurs over either HTTP (the Hypertext Transfer Protocol) or HTTPS (HTTP over Transport Layer Security).  HTTP communications are unencrypted, whereas HTTPS communications are encrypted.  It is generally advisable to use HTTPS anywhere it is available, *especially* when submitting sensitive information such as usernames and passwords.  [HTTPS Everywhere](https://www.eff.org/https-everywhere) is a browser plugin which attempts to force an HTTPS connection, and which can be set to block communications over HTTP entirely. 

## Use a Firewall

A ``firewall'' is a program which monitors the incoming and outgoing traffic on your network, and blocks requests based on rules set during its configuration.  Properly configured, a firewall can protect against some (but not all) attempts to remotely access your computer.

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

## Browser Settings

Browsers generally have a few simple settings which can be updated to increase privacy.  Specifically:

- Enable any built-in ad blockers.
- Send a "Do Not Track" message with all requests.
- Block third party cookies.

## Third Party Ad Blockers

In addition to built-in ad blockers, browser plugins have been built which block ads and tracking code.  [UBlock Origin](https://github.com/gorhill/uBlock/blob/master/README.md) and [Privacy Badger](https://www.eff.org/privacybadger) are widely used examples which can be used together or separately.

## Domain Name System (DNS) Encryption

DNS is the system by which a URL such as www.google.com is translated into an IP address such as 172.217.4.142.  Unfortunately, this protocol does not encrypt or authenticate the transaction, leaving us open to a number of security vulnerabilities.  [DNSCrypt](https://www.dnscrypt.org) solves this problem.

## Virtual Private Network (VPN)

Since the US congress has voted to [relax regulations](https://motherboard.vice.com/en_us/article/senate-republicans-vote-to-allow-isps-to-sell-your-private-data) preventing internet service providers (ISPs) from selling users' browsing histories, VPNs have become more important.  Choosing a VPN is a [complicated topic](https://arstechnica.com/security/2016/06/aiming-for-anonymity-ars-assesses-the-state-of-vpns-in-2016/), and may require a paid service depending on your circumstances.  A detailed comparison of the many available options can be found [here](https://thatoneprivacysite.net/vpn-section/), and a discussion on choosing a good VPN can be found [here](https://ssd.eff.org/en/module/choosing-vpn-thats-right-you).  But if you're just a casual user seeking to stick it to Comcast, check out [Opera](https://www.opera.com).  This lesser-known browser (a competetor to Firefox, Chrome, etc) has a built-in VPN called SurfEasy.  Currently, SurfEasy offers unlimited data use and pledges not to keep logs.  (There's got to be a catch somewhere, but I haven't found it yet.)

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
