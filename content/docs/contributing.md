---
title: 'Contributing to Sous Chefs'
date: 2018-11-28T15:14:39+10:00
---

We are glad you want to contribute to a sous-chefs cookbook! The first step is the desire to improve the project.

## Quick-contribute

- Create an issue on the GitHub issue tracker (see `issues_url` in the cookbook's `metadata.rb`)
- Link to your patch as a rebased git branch or pull request from the ticket

We regularly review contributions and will get back to you if we have any suggestions or concerns.

### Branches and Commits

You should submit your patch as a git branch named after the change.

It is a best practice to have your commit message have a _summary line_, followed by an empty line and then a brief description of the commit. This also helps other contributors understand the purpose of changes to the code.

Remember that not all users use Chef in the same way or on the same operating systems as you, so it is helpful to be clear about your use case and change so they can understand it even when it doesn't apply to them.

### GitHub and Pull Requests

We don't require you to use GitHub, and we will even take patch diffs attached to tickets on the issue tracker. However GitHub has a lot of convenient features, such as being able to see a diff of changes between a pull request and the main repository quickly without downloading the branch.

## Cookbook Testing

Each Sous Chefs cookbook is setup for both local testing and testing within Travis CI. We utilize [Cookstyle](https://github.com/chef/cookstyle), [Foodcritic](http://www.foodcritic.io/), and [Test Kitchen](http://kitchen.ci/) for complete cookbook testing. On a local workstation Test Kitchen will run via kitchen-vagrant against VirtualBox systems, while within Travis CI we utilize kitchen-dokken to test in Docker containers.

Prior to submitting your change you should run all tests. Linting (Cookstyle/Foodcritic) and Unit (ChefSpec) tests can be run by running `delivery local all`. Test kitchen tests can be run by running `kitchen test`. Test Kitchen tests may take quite some time to complete depending on the level of coverage and systems involved. You may want to run `kitchen list` and test against a sub-set of a total suites.

Any new functionality should include additional testing to protect against future regressions. Similarly, patches that fix a bug or regression should have a _regression test_. Simply put, this is a test that would fail without your patch but passes with it. The goal is to ensure this bug doesn't regress in the future. Consider a regular expression that doesn't match a certain pattern that it should, so you provide a patch and a test to ensure that the part of the code that uses this regular expression works as expected. Later another contributor may modify this regular expression in a way that breaks your use cases. The test you wrote will fail, signaling to them to research your ticket and use case and accounting for it.

If you need help writing tests, please ask on the [Community Slack](https://community-slack.chef.io/)

## Cookbook Contribution Do's and Don't's

Please do include tests for your contribution. If you need help, ask on the [Community Slack](https://community-slack.chef.io/)

Not all platforms that a cookbook supports may be supported by Test Kitchen. Please provide evidence of testing your contribution if it isn't trivial so we don't have to duplicate effort in testing. Chef 10.14+ "doc" formatted output is sufficient.

Please do indicate new platform (families) or platform versions in the commit message, and update the relevant ticket. If a contribution adds new platforms or platform versions, indicate such in the body of the commit message(s).

Please do use [Foodcritic](http://www.foodcritic.io/) and [Cookstyle](https://github.com/chef/cookstyle) to lint-check the cookbook, both of which are found in ChefDK.

Please do ensure that your changes do not break or modify behavior for other platforms supported by the cookbook. For example if your changes are for Debian, make sure that they do not break on CentOS.

Please do not modify the version number in the metadata.rb, the maintainer will select the appropriate version based on the release cycle information above.

Please do not update the CHANGELOG.md for a new version. Not all changes to a cookbook may be merged and released in the same versions. We will update the CHANGELOG.md when releasing a new version of the cookbook.
