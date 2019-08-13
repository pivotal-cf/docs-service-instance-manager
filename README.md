# Service Instance Manager (SIM) for PCF

## Where is the book repo?
https://github.com/pivotal-cf/docs-book-sim

The book repo uses these branches:

* **Edge** builds from the **master** content branch in this repo. Pipeline [here]().
* **Master** builds from the published content branches in this repo. Pipeline [here]().

## Branches in this (content) repo

### Master - Use for next unreleased version

All documentation for the next unreleased version of SIM is in `master`.

Always make changes you want carried forward in the master branch. This includes:

* Unreleased features
* Doc bug fixes
* Doc reorganization or enhancement

### Live Branches In Production (Public)

### Cherry picking to and from MASTER

1. Always cherry-pick any changes to live branches into **master** if you want those changes carried forward.

2. If necessary, immediately cherry-pick/copy changes from **master** that you want to push immediately to production into the appropriate live branch above.

### Style Sheet

We need to decide on product name short forms:
+ Longest name = **Service Instance Manager for Pivotal Cloud Foundry**
+ Long name if PCF has already been spelled out on the page = **Service Instance Manager for PCF**
+ Short name, use on the page after one of the long names has been used = **Service Instance Manager** or **SIM**?

## Pipelines

**Edge Pipeline**<br>
The `master` branch builds to the <br> <strong>cf-services-edge > sim-edge</strong> pipeline, and does not go to production until release time: [Edge pipeline](). <br>

[//]: # (**Production Pipeline**<br>
All live branches build to the <strong>cf-services > redis</strong> pipeline,
and are manually pushed to production as needed: [Production pipeline]().)

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
