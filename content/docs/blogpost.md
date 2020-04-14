---
title: 'Not Sure Yet'
date: "2020-04-14T00:00:00-00:00"
---

Sous-Chefs are a community orginasation and like to think of ourselves as a home for unloved great cookbooks and as a place where these can always get released moving forward.

While these cookbooks are great, they are not always in the best of places, and when we recieve them there is significant work to bring them up to our standards.

We also have all our existing cookbooks (of which there are over 70) and as all organisations our standards change and we need to reflect this across all of our repositores.

## Enter the bot army

We are an industry of DevOps practitioners and as part of that we aim to automate all of our world, and this is no exception. I have personally spent many hours trying to keep all of our files in sync across all the repositories we have.

To resolve this I have created 3 different bot applications

### Github-File-Manager

[Github File Manager](https://github.com/xorima/Github-File-Manager) is designed to ensure static files which do not change are consistent across all repositories, it uses a source repository and github topics to work out which repositores need these files to be put into them. They are issued as a PR and allow us to start having the important conversations about what our files should actually look like, rather than spending all the time trying to keep them the same.

For us our Source Repository is [Repo Management](https://github.com/sous-chefs/repo-management/tree/master/)

In here we look in the path `standardfiles/cookbook` and ensure these files are identicle in the discovered repositories, and if not the bot will issue Pull Requests to update the files

Examples of the files we manage:

- `Dangerfile`
- Github workflows
- Community files, such as Code of Conduct

### Github-Label-Manager

### Github-Cookstyle-Runner


## Running them

Automation is at the heart of every solution in this industry, so it’s not surprise that a Github bot was the best option. The one we chose was $whatever, and we chose it for $reasons. (or, if you wrote it, you talk about why you decided to write your own)
With the first run this week we did $x, $y, $z, and isn’t that neat?

## Future of the bot and sous-chefs

Our plans to expand this currently are limited to $zy, though we’d love to also be able to do $zx. If you have ideas to share, or just want to see what we’re up to, come join sous-chefs in the Chef slack.

