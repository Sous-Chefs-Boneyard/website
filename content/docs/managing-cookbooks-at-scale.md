---
title: 'Managing Cookbooks at Scale'
date: "2020-04-14T00:00:00-00:00"
---

Sous-Chefs are a community organisation and like to think of ourselves as a home for unloved great cookbooks and as a place where these can always get released moving forward.

While these cookbooks are great, they are not always in the best of places, and when we recieve them there is significant work to bring them up to our standards.

We also have all our existing cookbooks (of which there are over 70) and as all organisations our standards change and we need to reflect this across all of our repositores.

## Enter the bot army

We are an industry of DevOps practitioners and as part of that we aim to automate all of our world, and this is no exception. I have personally spent many hours trying to keep all of our files in sync across our repositories.

To resolve this I have created 3 different bot applications, these are designed to each tackle one problem we had with managing our multitude of cookbooks.

### Github-File-Manager

[Github File Manager](https://github.com/xorima/Github-File-Manager) is designed to ensure static files which do not change are consistent across all Repositories, it uses a source repository and github topics to work out which repositores need these files to be put into them. They are issued as a pull request and allow us to start having the important conversations about what our files should actually look like, rather than spending all the time trying to keep them the same.

For us our source repository is [Repo Management](https://github.com/sous-chefs/repo-management/tree/master/)

In here we look in the path `standardfiles/cookbook` and ensure these files are identical in the discovered repositories, and if not the bot will issue pull requests to update the files

Examples of the files we manage:

- [Dangerfile](https://github.com/danger/danger)
- [Github Actions](https://github.com/features/actions)
- [Community files](https://help.github.com/en/github/building-a-strong-community/creating-a-default-community-health-file), such as Code of Conduct

### Github-Cookstyle-Runner

[Github Cookstyle Runner](https://github.com/xorima/Github-Cookstyle-Runner) was created to solve the problem all orginisations with large amounts of cookbooks have.
> I know I am meant to run cookstyle, but I don't have time to.

This little app will find github repositories by Topic and run `cookstyle` against them, creating a pull request if changes are found with detailed messages for the changes, [example](https://github.com/sous-chefs/java/pull/606).

As an org we were very bad at keeping up to date with `cookstyle` fixes, which can unblock you, our users, from having failures on new versions of Chef Infra or in areas we made a mistake and just didn't realise.

### Github-Label-Manager

[Github Label Manager](https://github.com/xorima/Github-Label-Manager) is the final of the trio of bot applications we use to manage our repositories today, simply put it reads `json` files from a source repository, and ensures those labels (and optionally only those labels) exist on our cookbooks.

Now we could also have done this with our [Terraform Github Org](https://github.com/sous-chefs/terraform-github-org) however we found in the past that this caused us to run out of github API calls far too quickly when needing to make multiple terraform changes.

## Running them

Automation is at the heart of every solution in this industry, so it’s not a surprise that a docker image was the best option for a deployable artefact.

We decided to use kubernetes for deployment purposes simply for the fact that as an org we rely on contributors to give up their free time, and the less time we are burning on build systems, bots and release systems the more time we have to do what we exist for, high quality cookbooks.

With the first run this week across [sous-chefs](https://github.com/sous-chefs) and [chef-cookbooks](https://github.com/chef-cookbooks) orgs we opened over 300 pull requests and of those 257 have already been merged, imagine how much time that saves

## Future of the Bot and Sous-Chefs

- The apps themselves were written in a hackathon manner, which means almost no automated testing, so getting good testing is essential going forwards
- Extending the File-Manager to handle deletion of files and introducing a tempalting enginer to build out files as we need for our READMEs as an example.
- An automatic release system for our cookbooks, so one day a simple merge will automatically push these changes to the Supermarket, giving us more time to code and less time on maintenance.
- Migrating the release of these applications into a hart package instead of the current system of static kubernetes manifests

As always we are a group of volenteers and our doors are always open, so if you can help with any of this or want to get involved in some of the cookbooks we help to maintain, you can find us on the [Chef Community Slack](https://community-slack.chef.io/) the the `#sous-chefs` channel
