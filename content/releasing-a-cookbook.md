# So, you want to release a cookbook

First things first, you need to be a `collaborator` on the cookbook in the supermarket for which you wish to release.

## First, the basics

* Setup an account on <https://supermarket.chef.io>
* SuperMarket pem key saved locally, if you are just setting up, it will output the pem for you
* Install [stove](https://github.com/tas50/stove)

## Release checklist

* The version in the metadata.rb matches the version you're expecting to release
* The CHANGELOG.md has the latest version you're releasing and notes updated
* The tag doesn't exist yet in github, check `git tag` for it

## Finally, release

```bash
cd <cookbook git repo directory>
stove login --username <your-username> --key <path to your pem, possibly ~/.chef/username.pem>
stove # yep, it's that simple
```
