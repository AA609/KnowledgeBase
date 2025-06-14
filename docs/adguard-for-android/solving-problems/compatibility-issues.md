---
title: Known compatibility issues with Android apps
sidebar_position: 14
---

:::info

This article is about AdGuard for Android, a multifunctional ad blocker that protects your device at the system level. To see how it works, [download the AdGuard app](https://agrd.io/download-kb-adblock)

:::

## VPN apps

If you are using AdGuard in the *Local VPN* filtering mode, you cannot run other VPN apps at the same time. To solve this problem, we suggest that you:

- Use [AdGuard VPN](https://adguard-vpn.com/welcome.html) — its *Integrated mode* allows two apps to operate simultaneously
- Configure your VPN app to act as an [outbound proxy](../solving-problems/outbound-proxy.md) and set up a local outbound proxy using the parameters from the third-party app
- Switch to the *Automatic proxy* mode. When you do that, AdGuard will no longer use local VPN and will reconfigure iptables instead
-  به طرف طرف  *پروکسی راهنمای*  حالت. برای این کار، بروید  *Settings* → *فیلم برداری* → *شبکه* → *حالت حرکت*

: سازگاری

The *پروکسی خودکار*  حالت فقط در دستگاه های ریشه دار قابل دسترسی است. چون  *پروکسی راهنمای*در دستگاه هایی که در اندروید ۱۰ یا بعد از آن در اندروید ۱۰ یا بعد اجرا می شوند، ریشه گذاری لازم است.

:::

## DNS خصوصی

ویژگی خصوصی DNS در اندروید پی معرفی شد. قبل از نسخه Q، DNS خصوصی منطق فیلتر سازی AdGuard DNS را شکست و DNS که از طریق AdGuard به طور معمول کار می کرد. اما از نسخه Q، وجود DNS خصوصی برنامه ها را برای بازسازی ترافیک از طریق حل سیستم به جای آدگارد می کند. ببینید  [وبلاگ](https://android-developers.googleblog.com/2018/04/dns-over-tls-support-in-android-p.html)   برای جزئیات بیشتر 

-  برای حل مشکل با DNS خصوصی استفاده کنید  `شبکه دلار`  قانون

Some device manufacturers keep Private DNS settings hidden and set 'Automatic' mode as a default one. Thus, disabling Private DNS is impossible but we can make the system think that the upstream is not valid by blocking it with a `$network` rule. For instance, if the system uses Google DNS by default, we can add rules `|8.8.4.4^$network` and `|8.8.8.8^$network` to block Google DNS.

## Unsupported browsers

### UC Browsers: UC Browser, UC Browser for x86, UC Mini, UC Browser HD

To be able to filter HTTPS traffic, AdGuard requires the user to add a certificate to the device's trusted user certificates. Unfortunately, UC browsers don't trust user certificates, so AdGuard cannot perform HTTPS filtering there.

- To solve this problem, move the [certificate to the system certificate store](../solving-problems/https-certificate-for-rooted.md/)

:::note Compatibility

Requires root access.

:::

### Dolphin Browser: Dolphin Browser, Dolphin Browser Express

AdGuard cannot filter its traffic when operating in the *Manual proxy* mode because this browser ignores system proxy settings.

- Use the *Local VPN* filtering mode to solve this problem

### Opera mini: Opera mini, Opera mini with Yandex

Opera mini drives traffic through a compression proxy by default and AdGuard is not able to decompress and filter it at the same time.

- There is no solution at this moment

### Puffin Browser: Puffin Browser, Puffin Browser Pro

Puffin Browser drives traffic through a compression proxy by default and AdGuard is not able to decompress and filter it at the same time.

- There is no solution at this moment
