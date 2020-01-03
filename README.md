# Pivotal Service Instance Manager

## Where is the book repo?
https://github.com/pivotal-cf/docs-book-sim

The book repo uses these branches:

* **Edge** builds from the **master** content branch in this repo.
Pipeline [here](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?group=sim-edge).
* **Master** builds from the published content branches in this repo. Pipeline [here](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?group=sim).

## Branches in this (content) repo

All documentation for the next unreleased version of Service Instance Manager is in `master`.

Always make changes you want carried forward in the master branch. This includes:

* Unreleased features
* Doc bug fixes
* Doc reorganization or enhancement

| Branch Name| Use for… |
|------------| ---------|
| master     | v0.8 (staged here: http://docs-pcf-staging.cfapps.io/service-instance-manager/0-n/) |
| 0.7        | v0.7 (http://docs.pivotal.io/service-instance-manager/0-7/) |
| 0.6        | v0.6 (http://docs.pivotal.io/service-instance-manager/0-6/) |
| 0.5        | v0.5 (http://docs.pivotal.io/service-instance-manager/0-5/) |
| 0.4        | v0.4 (http://docs.pivotal.io/service-instance-manager/0-4/) |
| 0.3        | v0.3 (http://docs.pivotal.io/service-instance-manager/0-3/) |

### Cherry picking to and from MASTER

1. Always cherry-pick any changes to live branches into **master** if you want those changes carried forward.

2. If necessary, immediately cherry-pick/copy changes from **master** that you want to push immediately to production into the appropriate live branch above.

### Style Sheet

We need to decide on product name short forms:
+ Longest name = **Pivotal Service Instance Manager**
+ Short name, use on the page after the long name has been used = **Service Instance Manager**

## Pipelines

**Edge Pipeline**<br>
The `master` branch builds to the <br> <strong>cf-services-edge > sim-edge</strong> pipeline, and does not go to production until release time: [Edge pipeline](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?group=sim-edge). <br>

**Production Pipeline**<br>
All live branches build to the <strong>cf-services > sim</strong> pipeline,
and are manually pushed to production as needed: [Production pipeline](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?group=sim).

## How to Cherry-pick from one Branch to Another
1. Make changes in the first branch (usually `master`), commit them, and then push them to the repo.
2. Copy part of the SHA for the above commit. To find this, you can do a `git log`, or look at the list of commits in the github repo.
3. Checkout the second branch, where you want to copy the changes you made in the first branch.
4. Run this command, using the SHA snippet you copied above:
    `git cherry-pick <SHA_SNIPPET>`<br><br>
    For example: `git cherry-pick 5dc22fe00`

    Do the cherry-pick immediately to lessen the chances of conflicts.
    Otherwise, you may need to resolve conflicts in order to complete the cherry-pick.

5. Do a `git push` after the cherry-pick is complete.<br><br>
