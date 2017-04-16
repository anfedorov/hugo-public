+++
date = "2015-07-18"
menu = "main"
title = "Wildcards and SAN's in SSL certificates"
linktitle = "Wildcards and SAN's in SSL certs"
+++

### Prereqs

This post assumes you understand the general concepts underlying https and expounds on how certificates specify which domains they validate and summarizes the kind of certifications that Certificate Authorities (CA's) offer.

### Big-picture view

There are three layers of rules governing how https certs work, set by various standards bodies and private companies:

  - protocol specs from IETF like [TLS](https://tools.ietf.org/html/rfc5246) and [HTTP over TLS](https://tools.ietf.org/html/rfc2818),
  - publications of the [CA/Browser Forum (CABF)](https://cabforum.org/), and
  - published practices and internal policies specific to a CA.

The first are, for practical purposes, set in stone. The second are agreed upon regularly and evolve with time. The third can be negotiated and changed relatively easily.

### IETF specifications

According to the HTTP over TLS spec, certificates can specify the domains they validate to in two ways:

  - the Common Name (CN) field, and
  - the Subject Alternative Names (SAN) extension.

If you look at the certificate issued by google.com, you can see that it contains both:

{{< figure src="/img/wildcards-sans-in-ssl-certs/cert.png" >}}

(and a little further down)

{{< figure src="/img/wildcards-sans-in-ssl-certs/san.png" >}}

[RFC6125](https://tools.ietf.org/html/rfc6125#section-6.4.4) says the browser MUST NOT check the CN if a SAN is present, but some implementations do anyway. Chrome and Cloudflare follow this requirement and ignore the CN (i.e. they issue a cert error if the domain being validated is listed in the CA but not the SAN), while Safari and curl do not.

The `*` in `*.google.com` is a wildcard, and will match any single label before `.google.com`, such as `www.google.com` and `mail.google.com`. It will not match `google.com`, however, which is listed as a separate SAN entry in the google.com cert, below where the screenshot cuts off.

### Certificate Authorities in Practice

It costs a lot of money to implement the systems required to be a CA, but the costs of issuing certificates is wholly negligible, and so CA's set their prices based wholly on how many users are willing to pay a certain amount for a kind of certificate.

For an automated verification (e.g. sending an email to admin@foo.com to verify who controls foo.com), the total cost to a CA verifying and issuing a certificate is a fraction of what it costs to print a $1 bill, but it will currently cost you thousands of dollars per year to list as many wildcard entries in the SAN as Google does in their certificate.

As of the July 2015, there appear to be three general categories of certifications that CA's offer publicly:

{{< figure src="/img/wildcards-sans-in-ssl-certs/cost.png" >}}

Where

  - `FOO.COM` means any Fully-Qualified Domain Name (FQDN), which can include subdomains, like `blog.anfedorov.com` or `big.blog.anfedorov.com`,
  - `*.FOO.COM` means a domain with a single wildcard character, like `*.anfedorov.com` or `*.sandy.anfedorov.com`, and
  - `~` means varying within an order of magnitude (e.g. DigiCert offers wildcards for $500/yr).

Wildcards DNS records must have a single `*` in the leftmost label, so `blog.*.anfedorov.com` is not allowed. Only one wildcard can be present in a CN or SAN entry (so `*.*.foo.com` is not allowed). This is not a restriction of TLS [1], but of the rules CA's and browsers agreed on as part of the CA/Browser Forum's [Baseline Requirements](https://cabforum.org/baseline-requirements-documents/).

Wildcards will match any label, so a cert containing `*.anfedorov.com` will verify `mail.anfedorov.com` as well as `www.anfedorov.com`, and `*.sandy.anfedorov.com` will verify `1.sandy.anfedorov.com`, `2.sandy.anfedorov.com`, and so on. Neither of these will match `anfedorov.com`, however, which needs to be a separate SAN entry or its own domain.

The costs in the table above are taken from the base offers through namecheap.com, which negotiates them on your behalf. The price of a particular cert can factors in some other variables which are used mostly for price discrimination and have little practical significance.

The kind of certificate Google sends users (Multi Domain with wildcards in SAN entries) doesn't appear to be offered publicly by CA's, however at least one (DigiCert) tells me you can combine multiple wildcard certs into one with the domains listed in the SAN's by emailing their support team, i.e. pay them ~$500/year for each wildcard entry in the SAN. Google has their own intermediate cert from the GeoTrust root, so they don't have to pay to issue individual certs.

An alternative to the for-profit-CA business model is being explored by the [Internet Security Research Group](https://en.wikipedia.org/wiki/Internet_Security_Research_Group), a California Benefit Corporation run by a board associated with Mozilla, the EFF, Stanford, and the University of Michigan (as well as Cisco and Akamai). Their project is called [Let's Encrypt](https://letsencrypt.org/), and is scheduled to start giving out free Single Domain and Multi Domain certs later this year.

Please [let me know](mailto:me@anfedorov.com) if you spot any errors, outdated info, or omissions in this post. Also, if there is an obvious next topic to cover that isn't linked to from here, or if you have general feedback of any kind.

*Many thanks to the SSL Support Team at Namecheap for helping me along in figuring this out as well as to Jason Dusek, Christopher Hesse, Adam Pantel, Kamal Marhubi, and Greg Brockman for proofreading and providing feedback / corrections. This post is licensed under [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/).*

1. Some browsers will even accept a certificate with two wildcards in a SAN name: {{< figure src="/img/wildcards-sans-in-ssl-certs/two-wildcards.png" >}}

