+++
date = "2015-07-28"
menu = "main"
title = "VPN and WebRTC"
linktitle = "VPN and WebRTC"
+++

A [curious demo](https://www.privacytools.io/webrtc.html) where a web server sends you JS that sends back your internal network IP address via [the STUN protocol](https://en.wikipedia.org/wiki/STUN) intended to work around the structure of NAT's for peer-to-peer connections. What does that leak about a VPN connection?

Over PPTP:

{{< figure src="/img/PPTP.png" >}}

Well, that's worrying.

What about over L2TP?

{{< figure src="/img/L2TP.png" >}}

hm... and over OpenVPN?

{{< figure src="/img/openvpn.png" >}}

Well, that's somewhat comforting, at least.

`todo.add('learn how the VPN wizardry works')`
