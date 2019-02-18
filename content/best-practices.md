+++
author = "Dan Webb"
date = "2019-02-15T20:24:17-05:00"
description = "Coobkook Best Practices"
draft = false
keywords = ["cookbook","best practices"]
title = "Sous-Chefs Cookbook Best Practises"
topics = ["cookbook","best practices"]
type = "post"

+++

# Cookbook Best Practices

If we're adopting a cookbook and trying to bring it up to scratch, these are likely the first things people will expect.

## Platform Support

The majority of our survey userbase uses the following and as such as aim to support these platforms by default:

- Centos 6/7
- Debian 8/9
- Ubuntu 16.04/18.04
- Amazon 1/2

## Custom Resources over Attribute Driven

Our cookbooks are application cookbooks, and therefore designed to only manage a single type of application at a time. For example, a PostgreSQL server.

All configurablebles should be surfaced through a easy to understand, [custom resource](https://docs.chef.io/custom_resources.html) interface.

For example the [postgresql_client_install resource](https://github.com/sous-chefs/postgresql/#postgresql_client_install), surfaces a version atrribute. Which is obvious to the user. Much like a template, or file resource.

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
