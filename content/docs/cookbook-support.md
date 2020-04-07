---
title: 'Cookbook Support'
date: 2020-04-03T00:00:00+00:00
---

Cookbook support is a complicated subject based on many variables, however this document should outline expectations in our cookbooks

## Semver

We follow semver, this is never optional to our cookbooks, and allows you, our consumers, to understand the change we are making and the potential impact on your environment.

## Cookbook Support

We will attempt to support the version of the Chef Infra Client that Chef Software supports unless there is a compelling reason not to, such as:

- Features we require that are only in a later version of the Chef Infra Client
- Bugs which require a certain version of the Chef Infra Client
- Ruby versions which are closely tied to Chef Infra Client versions

However, as always, we welcome pull-requests to extend our support across multiple versions
