---
title: Protect origin IP address
pcx_content_type: learning-unit
weight: 1
layout: learning-unit
---

Though Cloudflare automatically hides your origin server IP address when you [proxy your DNS records](/learning-paths/prevent-ddos-attacks/baseline/proxy-dns-records/), there are other ways to discover an IP address.

To prevent attackers from discovering your origin's IP address, review the following suggestions.

## Rotate IP addresses

DNS records are in the public domain, meaning that - even though your IP addresses are hidden once you proxy your DNS records - someone could uncover historical records of your addresses.

For additional security, you could rotate the IP addresses of your origin server, which would also require [updating your DNS records](/dns/manage-dns-records/how-to/create-dns-records/#edit-dns-records) within Cloudflare.

## Review unproxied DNS records

Unproxied DNS records - also known as **DNS-only** records - can sometimes contain origin IP information, especially those used for FTP or SSH.

Review these records to make sure they do not contain origin IP information or use [Cloudflare Spectrum](/spectrum/) to proxy these records.

## Conceal unproxied DNS records

If you need to have **DNS-only** records that contain origin IP information, use non-standard names for these records. This action makes dictionary scans of your DNS less likely to expose your origin IP address.

For example, instead of `ftp.example.com`, you could use `827450184590183489.example.com` or `cloudflare-docs-are-great.example.com`.

## Evaluate mail infrastructure

{{<render file="_email-record-origin-ip.md">}}