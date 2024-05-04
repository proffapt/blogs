---
title: "IIT KGP Networking & Communication"
seoTitle: "Networking & Communication documentation, IIT Kharagpur"
seoDescription: "A thorough documentation on communication aspect of restrictions imposed on the network in IIT-KGP campus, discussing about the problem and their solutions."
datePublished: Thu Sep 22 2022 07:40:02 GMT+0000 (Coordinated Universal Time)
cuid: clfryl5v500000al81blbbd1t
slug: iit-kgp-networking-and-communication
canonical: https://gist.github.com/proffapt/0f032c3c48ec71b1c8dfe3f383b5431f
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714185523342/16291d19-7489-4ce9-9f41-e7a17dcbfe13.png
tags: network, social-media, iitkgp, iitkgpnetwork, network-documentation

---

# Introduction

The network on the campus of IIT Kharagpur has a speed of around 700Mbps via ethernet and 50-60Mbps via WiFi in rooms generally (tho in practice the speed is around 2-3 Mbps around the campus), well coming back to the topic. Even after all of this, it's so frustrating to use with heavy restrictions imposed on it; with UDP packets being completely dropped, common social media platforms (like WhatsApp, telegram, discord, etc) blocked, some Linux and Unix (will be referring both as \***nix** from now) repositories being blocked resulting in errors while updating/installing a package and many more Quoting the administration's reply on being asked upon this:

> "This is as per the institute's administrative policy decision. Sorry for this inconvenience."  
> Computer & Informatics Centre, IIT Kharagpur - Jul 28, 2022.

For a detailed analysis of the network and possible solutions as a whole read [IIT-KGP-NETWORK](https://github.com/sheharyaar/iit-kgp-network), exhaustive documentation on the network by my senior [Mohammad Shehar Yaar Tausif](https://github.com/sheharyaar). In this blog, we will be focusing on the communication aspect only, what all are blocked, and the most efficient method to unblock them along with some alternative platforms to shift you and your friends too - not gonna promote Telegram, I promise (￢‿￢ ).

# The problem

UDP traffic on standard ports is dropped; interfering with the internals of WhatsApp and maybe discord and telegram too; maybe it was intentional to keep us away from texting all day and focus on studies; not confirm tho but like all of this gonna stop us from using them somehow (￢‿￢ ).

### Status of various social media platforms:

| Name | Status |
| --- | --- |
| Telegram | ❌ |
| Whatsapp | ❌ |
| Discord | ❌ |
| Signal | ❌ |
| YouTube | ⚠️ |
| Slack | ⚠️ |
| Facebook | ✅ |
| Instagram | ✅ |
| LinkedIn | ✅ |
| Twitter | ✅ |
| Mastodon | ✅ |
| [Matrix.org](http://Matrix.org) | ✅ |
| Reddit | ✅ |

⚠️ - Limitations imposed

* `YouTube`: Restricted Mode - ON.
    
* `Slack`: Only the desktop client works.
    

Though the restrictions are surprising; blocking WhatsApp on the one hand and leaving Facebook and Instagram on the other doesn't seem to fit into any ideology. Anyways let's discuss some possible solutions and their feasibility.

# The Solution

## 1\. Using VPNs

Not this much easy, for obvious reasons; most of them are blocked as they rely on UDP, for details on which are blocked and which are not have a look at:

* [Non-technical, straightforward documentation](https://github.com/sheharyaar/iit-kgp-network/blob/main/README_general.md)
    
* [Technical documentation](https://github.com/sheharyaar/iit-kgp-network/blob/main/README_technical.md)
    

This is the only possible way to use the following platforms:

* Whatsapp
    
* Discord
    
* Signal
    

## 2\. Telegram and Proxy

This section is dedicated to telegram and its versatility - the way you will only be configuring proxy on telegram and using the network at its full potential everywhere else - with its proxy protocol namely MTProto; tho it provides other types of proxies too, for example, SOCKS5, HTTPS, etc. none of them will work except MTProto. It was developed solely for enhancing the user experience on weak network connections and now we can utilize it for accessing telegram API through the campus network. For technical details on how it works behind the scenes (as much it is available in the public domain) refer to:

* [MTProto - Telegram core](https://core.telegram.org/mtproto)
    
* [MTProto - wikidata](https://www.wikidata.org/wiki/Q18558947)
    

### Security Aspect

Read the below documentation thoroughly and then only comment on its security and decide whether to use it or not depending on your [threat model](https://owasp.org/www-community/Threat_Modeling).

* [Telegram Cryptoanalysis Contest - Crypto Fails](https://www.cryptofails.com/post/70546720222/telegrams-cryptanalysis-contest)
    
* [On the CCA (in)security of MTProto](https://eprint.iacr.org/2015/1177.pdf)
    

### How to configure a proxy?

Refer to either of the sections below, depending on your currently available knowledge and comfortability with this type of technology.

#### Have no idea what proxies are

1. Go to [Proxy Monitoring Bot](https://t.me/mtpro_xyz_bot).
    
2. Type `/mtproto` in the chat box.
    
3. Click on any of the proxies, given to you in reply; try a few and find the fastest one for you.
    
4. Select the check box `Enable Proxy` in the popup window; if any.
    
5. Select `Add Proxy` and done.
    

> If still facing some issues, then manually add those proxies via the method described next.

#### Have some idea what proxies are

If you know what proxies are, and you wanna configure your own custom one - be it self-hosted or whatever - follow these steps:

1. Go to Settings -&gt; Data & Storage -&gt; Use proxy (path being same on Android, MacOS, Windows, and Linux).
    
2. Choose your proxy from the resources below or use the details of your proxy.
    

* [https://t.me/prxlst](https://t.me/prxlst)
    
* [https://proxypage.io/](https://proxypage.io/)
    
* [https://mtproto.co/](https://mtproto.co/)
    

1. Select the proxy type as MTPROTO.
    
2. Add the IP for the proxy server in the field named `Server`.
    
3. Enter the port being used by the proxy in the field named `Port`.
    
    > Enter `username` and `password`, if any.
    

### Observations

It is reliable and secure (not cracked yet, all those attacks which you might have read from the docs in [Security Aspect](#security-aspect) are theoretical and have not been performed successfully yet).

* Direct calls are supported.
    
* VC and group calls are not supported.
    

## 3\. Using Web Versions

* You can utilize the web versions of your desired platforms to unblock them via, browser-based proxies like [HoxxVPN](https://chrome.google.com/webstore/detail/hoxx-vpn-proxy/nbcojefnccbanplpoffopkoepjmhgdgh), [SetupVPN](https://chrome.google.com/webstore/detail/setupvpn-lifetime-free-vp/oofgbpoabipfcfjapgnbbjjaenockbdp), etc but these are **unsafe** to use.
    
* One can also use the [Opera Browser](https://www.opera.com/?utm_campaign=%2307%20-%20IN%20-%20Search%20-%20EN%20-%20Branded%20-%202017) which comes with an inbuilt proxy - see [Free VPN - Opera](https://www.opera.com/features/free-vpn) - this is named as "VPN" by opera but, it is not, it's a fork of SurfEasy proxy which was bought by Opera ([source](https://forums.opera.com/topic/35383/is-the-vpn-a-true-encrypted-vpn-or-just-a-proxy/4)). Not much usable for streaming since it is very very slow (comparable to the speed of TOR).
    
* A much more "secure" option than the previous ones is [Tor via Brave Browser](https://support.brave.com/hc/en-us/articles/360018121491-What-is-a-Private-Window-with-Tor-Connectivity-), tho I am not clear about the exact level of security but it's safer than others for sure and a hell lot slow for surfing - can stream videos at 1080p on youtube without buffer tho :). One drawback, which is a real problem; you will have to log in every damn time as there will be no cookie stored for your sessions.
    

## 4\. Use alternatives

Since the solutions are limited, then a good strategy might be to shift to another working platform like Telegram, slack, and [Matrix.org](http://Matrix.org). Facebook is **NOT** suggested with its poor track record, lots of data leaks, bad privacy policy, and whatnot.

* [Reasons not to `be used by` Facebook](https://stallman.org/facebook.html)
    
* [Matrix.org](http://Matrix.org)
    

Telegram and [Matrix.org](http://Matrix.org) are my personal choice of alternatives; with telegram being unblocked via its inbuilt proxy configuration and [matrix.org](http://matrix.org) staying useful without any configuration.

> For people planning to shift to or already there on **telegram** consider joining: [@projecttrik](https://t.me/projecttrik) for more details on features and use cases of Telegram, just an initiative by me to make the users understand the potential of telegram.

Now you have a basic idea about the approaches, decide according to your use case and [threat model](https://owasp.org/www-community/Threat_Modeling).