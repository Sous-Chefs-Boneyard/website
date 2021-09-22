---
title: "2018 In Review"
date: "2018-12-31"
---

Hello, this is Joseph Holsten & Dan Webb from Sous Chefs. We've had quite a year, so I thought I'd summarize the major moments. Here we go!

2018 was a pretty big year in Sous-Chefs, we started on [OpenCollective](https://opencollective.com/sous-chefs) to raise funds for our core contributors. Many hours go into rewriting, maintaining, and reviewing pull requests. It's a great way to give back to those that empower you and your company!

We moved our cookbook testing from TravisCI to CircleCI accross the board, for reliability and speed reasons. We were one of the first organisatons to adopt [Orbs](https://circleci.com/orbs/). Orbs are a way of reusing commands and more importantly yaml, without losing the expressiveness that comes with CircleCI. Check ours out [here](https://github.com/sous-chefs/orbs).

## Major/New Releases

- [`Postgresql`](https://github.com/sous-chefs/postgresql/blob/main/CHANGELOG.md) - This was the biggest release of the year, Completely rewritten with custom resources and a full unit and functional test suite. ([@damacus](https://github.com/damacus)/[@martinisoft](https://github.com/martinisoft))
- [`Redisio`](https://supermarket.chef.io/cookbooks/redisio) - Major release & new maintainers! ([@tas50](https://github.com/tas50)/[@majormoses](https://github.com/majormoses)/[@shoekstra](https://github.com/shoekstra))
- [`vscode`](https://supermarket.chef.io/cookbooks/sc_vscode) - First version of the [vscode cookbook](https://github.com/sous-chefs/vscode) was released by ([@Xorima](https://github.com/Xorima))
- [`sc-chruby`](https://supermarket.chef.io/cookbooks/sc-chruby) Released late in 2018 by [@damacus](https://github.com/damacus)

## Adoptions

- [`java`](https://supermarket.chef.io/cookbooks/java)
- [`php`](https://supermarket.chef.io/cookbooks/php)
- [`squid`](https://supermarket.chef.io/cookbooks/squid)
- [`stunnel`](https://supermarket.chef.io/cookbooks/stunnel)
- [`confluence`](https://github.com/sous-chefs/confluence)

## Looking for an interesting challenge

The following cookbooks are currently underloved, but with a small number of community members. We know they've provided value to poeple in the past, but require some love.

- [`hashicorp-vault`](https://www.github.com/sous-chefs/hashicorp-vault)
- [`consul`](https://www.github.com/sous-chefs/consul)
- [`nexus`](https://www.github.com/sous-chefs/nexus)
- [`aptly`](https://www.github.com/sous-chefs/aptly)
- [`winrm`](https://www.github.com/sous-chefs/winrm)
- [`kismet`](https://www.github.com/sous-chefs/kismet)
- [`sensors`](https://www.github.com/sous-chefs/sensors)
- [`reprepro`](https://www.github.com/sous-chefs/reprepro)

## Now included in Chef 14

Both the `sysctl` and `swap` cookbooks are now included in Chef 14!

- [Chef 14 Release note](https://docs.chef.io/release_notes.html#new-resources)
- [Chef 14 CHANGELOG](https://github.com/chef/chef/blob/main/CHANGELOG.md#v140190-2018-04-03)

## Deprecated cookbooks

We've deprecated the mac_os_x cookbook in favour of the excellently written [MacOS cookbook from Microsoft](https://github.com/Microsoft/macos-cookbook).

[Chef Compliance](https://docs.chef.io/chef_compliance.html) was deprecreated as it's encorporated into Chef Automate. Our accompanying [cookbook](http://supermarket.chef.io/cookbooks/chef-compliance) has been deprecated.

## Too Many To Note

We've done a lot of releases in the past year, here's an absolutely huge list of all the "minor" releases.

- [`apache2`](https://supermarket.chef.io/cookbooks/apache2)
- [`atom`](https://supermarket.chef.io/cookbooks/atom)
- [`control_groups`](https://supermarket.chef.io/cookbooks/control_groups)
- [`dhcp`](https://supermarket.chef.io/cookbooks/dhcp)
- [`dnsmasq`](https://supermarket.chef.io/cookbooks/dnsmasq)
- [`filesystem`](https://supermarket.chef.io/cookbooks/filesystem)
- [`gpg`](https://supermarket.chef.io/cookbooks/gpg)
- [`grafana`](https://supermarket.chef.io/cookbooks/grafana)
- [`haproxy`](https://supermarket.chef.io/cookbooks/haproxy)
- [`line`](https://supermarket.chef.io/cookbooks/line)
- [`mariadb`](https://supermarket.chef.io/cookbooks/mariadb)
- [`sc-mongodb`](https://supermarket.chef.io/cookbooks/sc-mongodb)
- [`mysql`](https://supermarket.chef.io/cookbooks/mysql)
- [`nagios`](https://supermarket.chef.io/cookbooks/nagios)
- [`nrpe`](https://supermarket.chef.io/cookbooks/nrpe)
- [`sc-nxlog`](https://supermarket.chef.io/cookbooks/sc-nxlog)
- [`ossec`](https://supermarket.chef.io/cookbooks/ossec)
- [`openvpn`](https://supermarket.chef.io/cookbooks/openvpn)
- [`pulledpork`](https://supermarket.chef.io/cookbooks/pulledpork)
- [`ruby_rbenv`](https://supermarket.chef.io/cookbooks/ruby_rbenv)
- [`samba`](https://supermarket.chef.io/cookbooks/samba)
- [`selinux_policy`](https://supermarket.chef.io/cookbooks/selinux_policy)
- [`snort`](https://supermarket.chef.io/cookbooks/snort)
- [`unbound`](https://supermarket.chef.io/cookbooks/unbound)
- [`unifi`](https://supermarket.chef.io/cookbooks/unifi)
- [`vagrant`](https://supermarket.chef.io/cookbooks/vagrant)
- [`varnish`](https://supermarket.chef.io/cookbooks/varnish)
- [`zabbix-agent`](https://supermarket.chef.io/cookbooks/zabbix)
- [`chef_zfs`](https://supermarket.chef.io/cookbooks/chef_zfs)
