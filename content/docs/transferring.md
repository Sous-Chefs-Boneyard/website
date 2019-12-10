---
title: 'Transferring to Sous Chefs'
date: 2018-11-28T15:14:39+10:00
---
Got a cookbook you'd like help with? We'd love to help!

## Before you begin

We need to work with the GitHub repo owner and supermarket cookbook owner. If you aren't this person, let us know and we'll try to contact them. If necessary, fine beverages and chocolate chip cookies may be provided to encourage them to work with us.

When this is not possible please see [forking]({{< ref "forking.md" >}})

You'll need:

- `name` - base cookbook name
- `repo_url` - code repository URL
- `supermarket_name` - Supermarket cookbook name

## Joining Sous-Chefs

In order to transfer a cookbook into the sous-chefs organization on GitHub you must first become a member of the organization. See [becoming a member]({{< ref "becoming-a-member.md" >}}) for information on how to do this yourself.

## Transferring the code

Cookbook code may live in a number of places, here's what to do when the code is:

### From a single-cookbook repo in GitHub

- From the `repo_url` in GitHub
- Go to the **Settings** page
- Scroll down to the **DangerZone** and click **Transfer**
- Enter the appropriate **repo name** and for the **New owner's GitHub username or organization name** enter `sous-chefs`
- Click **I understand, transfer this repository.**

### From a monolithic repo in GitHub

There's the script to extract a cookbook's history from a monolithic repo. Then upload to new repo under sous-chefs.

- Create a GitHub repo for the cookbook with owner:`sous-chefs` and name:`${name}`
- Clone the monolithic to a local repo `git clone ${repo_url}`
- Extract the history of the desired cookbook from the repo: `git filter-branch --tag-name-filter cat --prune-empty --subdirectory-filter ${name} -- --all`
- Add the GitHub repo as a remote `git remote add sous-chefs https://github.com/sous-chefs/${name}.git`
- Push `git push sous-chefs --all` and `git push sous-chefs --tags`

This is adapted from "[How to extract a single file with its history from a git repository](https://gist.github.com/ssp/1663093)" by [ssp](https://github.com/ssp)

### From a non-GitHub repo

- Create a GitHub repo for the cookbook with owner:`sous-chefs` and name:`${name}`
- Clone the cookbook to a local repo `git clone ${repo_url}`
- Add the GitHub repo as a remote `git remote add sous-chefs https://github.com/sous-chefs/${name}.git`
- Push `git push sous-chefs --all` and `git push sous-chefs --tags`

## Have the proper GitHub user rights setup

Once the cookbook has been transferred a Sous-Chefs board member can setup the proper permissions for the repo

- Add a new GitHub team with the same name as the cookbook
- Add maintainers to that group
- Add that team to the repo with **Admin** privileges

Alternatively you can start this process yourself by sending a pull request to <https://github.com/sous-chefs/terraform-github-org>

## Transferring the cookbook in Supermarket

- From the cookbook's page in Supermarket click **Manage Cookbook** and select **Transfer Ownership**
- Make sure to check "Make current owner a collaborator?" to retain your access to the cookbook
- Enter `sous-chefs` and click **Transfer**

## Ensure consistent cookbook name

In case it isn't already, rename the repo to `https://github.com/sous-chefs/${name}.git`

- From the repo page on GitHub click **Settings**
- Under **Repository name** enter a new name and click **Rename**

## Cleanup links to the old home

There are probably many references to the old URLs out there in the world. Some places to check

- Update the `README.md` with a link to the current repo and supermarket page
- In `metadata.rb`:

    ```ruby
    source_url "https://github.com/sous-chefs/#{name}"
    issues_url "https://github.com/sous-chefs/#{name}/issues"
    maintainer 'Sous Chefs'
    maintainer_email 'help@sous-chefs.org'
    ```

## Migrate to circleci testing

[Circleci](https://circleci.com) is used for testing cookbooks. There are many examples of Circleci config in the sous-chefs org. If you need further assistance, post in the sous-chefs slack channel!
