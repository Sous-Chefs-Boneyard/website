---
title: 'Cookbook Best Practices'
date: 2018-11-28T15:14:39+10:00
---

If we're adopting a cookbook and trying to bring it up to scratch, these are likely the first things people will expect.

## Platform Support

We will attempt to support all operating systems releases currently supported by the OS vendor except where there is a compelling reason not to.

Current major operating system support lies in the following:

- Centos
- Ubuntu
- Redhat
- Amazon Linux 2
- macOS
- Windows

Some cookbooks are not designed to support all of these operating systems. For a full list of supported operating systems please refer to the `kitchen.yml` in the cookbook in question

## Custom Resources over Attribute Driven

Our cookbooks are application cookbooks, and therefore designed to only manage a single type of application at a time. For example, a PostgreSQL server.

All configurables should be surfaced through a easy to understand, [custom resource](https://docs.chef.io/custom_resources.html) interface.

For example the [postgresql_client_install resource](https://github.com/sous-chefs/postgresql/#postgresql_client_install), surfaces a version property. Which is obvious to the user. Much like a template, or file resource.

```ruby
postgresql_client_install 'Client install' do
  version '9.5'
end
```

## Resource Documentation

README docuemntation can get very long and hard to navigate. Splitting information down into easily digestable information is crucial in users being able to effectively use the cookbook.

Example structure:

```text
README.md
── documentation
│   ├── resource_apache2_conf.md
│   ├── resource_apache2_config.md
│   ├── resource_apache2_default_site.md
│   ├── resource_apache2_install.md
│   ├── resource_apache2_mod.md
│   ├── resource_apache2_module.md
│   └── resource_apache2_site.md
```

- The README.md should have links to both resource documents
- The resource documentation should have the following headings:
  - resource title
  - a table of available properties
  - a set of examples using the resource

## Semver

Our cookbooks follow semver guidelines. See [the semver spec](https://semver.org/spec/v2.0.0.html) for an overview. Semver allows allows cookbook consumers to better understand what version increments mean and plan their testing regiment accordingly
