---
title: 'Cookbook Best Practices'
date: 2020-04-03T00:00:00+00:00
---

Cookbook support is a complicated subject based on many variables, however this document should outline expectations in our cookbooks

## Semvar

We follow semvar, this is never optional to our cookbooks, and allows you, our consumers, to understand the change we are making and the potential impact on your environment.

## Cookbook Support

We will attempt to support the version of the `chef-client` that chef support unless there is a compelling reason not to, such as:

- Features we require that are only in a later version of the chef client
- Bugs which reqiure a certian version of the chef client
- Ruby versions which are closely tied to chef version

However as always we wecome pull-requests to extend our support across multiple versions
