---
title: 'Becoming a Member'
date: 2018-11-28T15:14:39+10:00
---

Join us on the [Chef community slack](https://chefcommunity.slack.com/messages/sous-chefs/), and say hi!

- Go to: [`terraform-github-membership/terraform.tfvars.json`](https://github.com/sous-chefs/terraform-github-membership/blob/main/terraform.tfvars.json) in the terraform-group-membership repo.

- Click the pencil to "Edit this file"

- To the file, add a line to the bottom of the `maintainers` section for your github user. If your username was `dmr`, you would add:

```json
{
  "board": [
    "..."
  ],
  "bots": [],
  "maintainers": [
    "...",
    "dmr"
  ]
}
```

- Write a commit message. For the above, a reasonable message might be `org_membership: add dmr`

- Select **Create a new branch for this commit and start a pull request**. (You're welcome to enter a branch name, but the default is also just fine!)

- Click **Propose File Change** to go to the "Open a Pull Request" page

- Click **Create Pull Request** (You're also welcome to change the title or description, but the default is still just fine!)

If there is a cookbook you wish to become a maintainer of then add yourself to that repo's corresponding file e.g. for `mongodb`, add yourself to `mongodb.tf` (of course after discussing it in slack).

**If you aren't comfortable with this:** that's okay! It doesn't matter if you're prefer to remain anonymous, or are uncomfortable writing code, or aren't ready for this level of commitment, you still can help out. You don't need to be in the membership configuration to join us in the [Chef community slack](https://chefcommunity.slack.com/messages/sous-chefs/). We'll be happy to find a way to contribute that everyone is comfortable with.
