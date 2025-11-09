---
title: Securing - Home Assistant
description: Instructions on how to secure your Home Assistant installation.
source_url: https://www.home-assistant.io/docs/configuration/securing
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:05:49.172Z
---

One major advantage of Home Assistant is that it is not dependent on cloud services. Even if you are only using Home Assistant on a local network, you should take steps to secure your instance.

## Checklist

Here’s the summary of what you _must_ do to secure your Home Assistant system:

- Centralize sensitive data in [secrets](https://www.home-assistant.io/docs/configuration/secrets/) (but do remember to back them up).

  - **Note**: Storing secrets in `secrets.yaml` does not encrypt them.
- Regularly keep the system up to date.

## Remote access

If you want secure remote access, the easiest option is to use [Home Assistant Cloud](https://www.home-assistant.io/cloud/) by which you also support the [Open Home Foundation](https://www.openhomefoundation.org/), which develops Home Assistant, ESPHome and much more.

Another option is to use TLS/SSL via the add-on [Duck DNS](https://www.home-assistant.io/integrations/duckdns/) integrating Let’s Encrypt.

To expose your instance to the internet, use a [VPN](https://pivpn.io/), or an [SSH tunnel](https://www.home-assistant.io/blog/2017/11/02/secure-shell-tunnel/). Make sure to expose the used port in your router.

### Extras for manual installations

Besides the above, we advise that you consider the following to improve security:

- For systems that use SSH, set `PermitRootLogin no` in your sshd configuration (usually `/etc/ssh/sshd_config`) and use SSH keys for authentication instead of passwords. This is particularly important if you enable remote access to your SSH services.
- Lock down the host following good practice guidance, for example:
  - [Securing Debian Manual](https://www.debian.org/doc/manuals/securing-debian-manual/index.en.html) (this also applies to Raspberry Pi OS)
  - [Red Hat Enterprise Linux 7 Security Guide](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/index), [CIS Red Hat Enterprise Linux 7 Benchmark](https://www.cisecurity.org/cis-benchmarks/)

## Related topics

- [Configuration.yaml](https://www.home-assistant.io/docs/configuration/)
- [Secrets.yaml file](https://www.home-assistant.io/docs/configuration/secrets/)
- [Home assistant cloud](https://www.home-assistant.io/cloud/)

## Related links

- [Nabu Casa](https://nabucasa.com/config/)

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/configuration/securing.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fconfiguration%2Fsecuring%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fconfiguration%2Fsecuring%2F%22&in=body "View given feedback for this page")
