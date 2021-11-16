---
title: 'Auto Releasing Sous-Chefs Cookbooks'
date: "2021-01-01T00:00:00-00:00"
---

[Sous-Chefs](http://sous-chefs.org/) is a [community funded](https://opencollective.com/sous-chefs) organisation and we like to think of ourselves as a home for unloved great cookbooks. We are also a place where these cookbooks will always get maintained moving forward.

While these cookbooks are great, when we typically take over management of the cookbook repos they are not in the best of states, and there is significant work to bring them up to our standards.

We also have all our existing cookbooks (of which there are over 70) and as our standards change, we need to deploy these changes across all of our repositories.

## Enter Automation

Earlier in the year we build the [Xorimabot backend suite](https://sous-chefs.org/docs/managing-cookbooks-at-scale/)

We now have cookbooks which are constantly getting updated but moved onto the next problem, releasing these is a manual process which takes time from our various contributors (Which normally is [Ramereth](https://github.com/Ramereth)).

Here we truly believe all members of the community should be able to release cookbooks as long as the normal checks (CI, Review) are passed so we did what any DevOps team would do, we built automation.

### Architecture

We started to partition the problem into smaller parts, below you can see the architecture we came up with in the end.
These applications currently run on Kubernetes, the aim is to migrate them to AWS Lambda simply due to the costs of running this solution. If you would like to aid us with covering the costs of sous-chefs donations would be welcome in our [Open Collective](https://opencollective.com/sous-chefs)

![Sous-Chefs auto release architecture](/images/automation-architecture.png)

In this architecture we have applications that cover the various problems we foresaw, these are covered in more detail below.
These applications uses github`s webhooks and APIs to run the applications automatically, we also enforce [HMAC secrets](https://docs.github.com/en/free-pro-team@latest/developers/webhooks-and-events/securing-your-webhooks) for additional security

## Label Validator

[Label Validator](https://github.com/Xorima/labelvalidator) is designed to ensure that we have a single `Release:` label on the pull request. The allowed labels are:

- Release: Major
- Release: Minor
- Release: Patch

These labels are important as other applications use them later on to determine the level of change we should be doing on the release. The results of this check are published back as a status check against the PR, allowing us to enforce this check must pass in order to proceed.

## Changelog Validator

[Changelog Validator](https://github.com/Xorima/changelog_validator) is designed to ensure that we have an `## Unreleased` heading in the changelog. This is where contributors should be putting their change notes. The changes to this file are enforced by [Danger](danger.systems/)

The `## Unreleased` section is used in later compontents (Cookbook Release Creator) to identify where in the changelog we should be updating. The results of this check are published back as a status check against the PR, allowing us to enforce this check must pass in order to proceed.

## Metadata Validator

aka: Cookbook Release Validator

[Metadata Validator](https://github.com/Xorima/cookbook_release_validator) is designed to ensure that the version number in the changelog is the same as the default branch. We manage this version with the Cookbook Release Creator application. The reason we check the individual line is because other items in the metadata may be changed during a PR.

The results of this check are published back as a status check against the PR, allowing us to enforce this check must pass in order to proceed.

## Cookbook Release Creator

[Cookbook Release Creator](https://github.com/Xorima/cookbook_release_creator) runs when a pull request is merged into the default branch. It then does a number of automated items for us:

- Set the new `metadata.rb` version based on the `Release: Major|Minor|Patch` label.
- Updates the Changelog with a release version heading based on the same label.
- Creates a [Github Release](https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/managing-releases-in-a-repository) on the repository, this will allow users to follow releases in Github for cookbooks they care about
  - A link to the release is also put as a comment on the merged PR
- Creates a [Github Deployment](https://docs.github.com/en/free-pro-team@latest/rest/reference/repos#deployments) Request via the Github Api
  - This deployment holds the release notes we will need for the Slack Notifier later on in the custom Payload attribute

## Cookbook Supermarket Uploader

[Cookbook Supermarket Uploader](https://github.com/Xorima/cookbook_supermarket_uploader) runs when a deployment is requested. It does the following:

- Checks the Deployment was created by the same user it is running as
- Clones the git code based on the tag which is pushed when a release is created
- Runs a `knife supermarket share` to upload this to the chef supermarket
- Posts back a sucessful or failed deployment to Github's API

## Slack Notifier

[Deployment Status Slack Notifier](https://github.com/Xorima/deployment_status_slack_notifier) runs when a [Deployment Status](https://docs.github.com/en/free-pro-team@latest/rest/reference/repos#list-deployment-statuses) is updated to Success of Failure. It then route the message to the [Chef Community Slack](https://community-slack.chef.io/). It gets the release notes from the payload of the deployment and posts them to `#Sous-Chefs` and `#Announcements`

## Future of the Automation and Sous-Chefs

These applications are already critical to our management infrastructure, and we have many plans for their future.

- Migrate these applications to AWS Lambda to reduce costs
- Add a notification to the slack discorse
- Create a dashboard, because metrics

As always we are a group of volunteers and our doors are always open. If you would like to help with any of our projects or want to get involved in some of the cookbooks we help to maintain, you can find us on the [Chef Community Slack](https://community-slack.chef.io/) the the `#sous-chefs` channel.
