# subtree-sample-master-repo
This lab explains how to merge code from a Git repo into another Git repo. This is useful to reuse assets that exists in a repo, hence avoiding manualy manually copying assets into multiple places. For instance: an API Common proxy with reusable policies or code fragments.

Based on [About Git Subtree merges](https://help.github.com/articles/about-git-subtree-merges/).

#### Step 1: Clone this repo
```bash
$ git clone https://github.com/dzuluaga/subtree-sample-master-repo.git

```

#### Step 2: ```$ cd subtree-sample-master-repo```

#### Step 3: Add common-repo remote

```bash
$ git remote add -f common-repo https://github.com/dzuluaga/subtree-sample-common-repo.git
```

#### Step 4: Merge the common-repo project into the local Git project
```bash
$ git merge -s ours --no-commit common-repo/master
```

#### Step 5: Create a directory to copy common-repo
Create a new directory called common-repo-assets, and copy the Git history of the common-repo project into it.
```bash
$ mkdir common-repo-assets
$ git read-tree --prefix=common-repo-assets/ -u common-repo/master
```

#### Step 6: Commit the changes to keep them safe
```bash
$ git commit -m "Subtree merged in common-repo-assets"
$ git push
```

### Synchronizing with updates and changes

```bash
$ git pull -s subtree remotename branchname
```

Example:
```bash
$ git pull -s subtree common-repo master
```