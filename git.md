
# git

Git is a free and open source distributed version control system.

## some command-line examples


### list branches

list local branches - the current branch will be highlighted with an asterisk
```
$ git branch
```


### rename a branch

rename the current local branch
```
$ git branch -m <new-branch-name>
```

rename a local branch - if you are on a different branch
```
$ git branch -m <old-branch-name> <new-branch-name>
```

if you have renamed a branch which also exists remotely...
```
$ git push origin :old-name new-name # delete the old-name remote branch and push the new-name local branch

$ git branch new-name # switch to the branch
$ git push origin -u new-name # reset the upstream branch for the new-name local branch

```

### switch branch

be careful - check if you have modified any files in the current branch before doing a checkout

switch to another local branch-name or tag-name
```
$ git checkout <branch-name>
```


### create a branch

generate and switch to new local branch-name
```
$ git checkout -b <new-branch-name>
```


### merge a branch

merge a local branch-name into the branch master
```
$ git status # just to confirm that you are on branch master
$ git merge <branch-name>
```


### delete a branch

delete a local branch-name
```
$ git branch -d <branch-name>
```

delete a remote branch-name
```
$ git push origin --delete <branch-name>
```


### create a tag

create a tag on current branch - before doing this you should have saved any local change (commit & push).
```
$ git tag -a 1.1 -m "my commit message"
$ git push --tags
```


### list branch commits/revisions

show a list of all commits/revisions for the current local branch
```
$ git log
```

the oneline option prints each commit on a single line, which is useful if you’re looking at a lot of commits
```
$ git log --pretty=oneline
```

#### limiting Log Output

show a list of the last 2 commits/revisions for the current local branch
```
$ git log -2
```

show a list of the any commits/revisions for the current local branch in the last 2 weeks
```
$ git log --since=2.weeks
```

more tips:
* you can specify a specific date like "2018-01-01"
* the --author option allows you to filter on a specific author
* to prevent the display of merge commits cluttering up your log history, simply add the log option --no-merges

#### searching the logs

show list of every revision/change/commit to that file
```
$ git log -p <path-to-file>
```

show list of every revision/change/commit to that file, within the specified range of line numbers
```
$ git log -L <start-line>,<end-line>:<path-to-file>
```

the git log command accepts the -S option, which looks for the code change (additions or deletions) for the specified string as an argument to the command - git actually parses all of the revisions in the repo to match the string
```
$ git log -S '<string-to-search-for>'
```


## reasons to use git

### for developers
* Feature Branch Workflow
  * One of the biggest advantages of Git is its branching capabilities. Unlike centralized version control systems, Git branches are cheap and easy to merge. This facilitates the feature branch workflow popular with many Git users.
  * The feature branch workflow also provides flexibility when priorities change. For instance, if you’re halfway through a release cycle and you want to postpone one feature in lieu of another time-critical one, it’s no problem. That initial feature can sit around in its own branch until engineering has time to come back to it.
  * ability to do commits on a feature branch before a change is complete. Because of this you can commit more often. It doesn't matter because other people won't see them until you publish.
* Collaboration Before Public Commits
  * Many source code management tools enhance core Git functionality with pull requests, which let developers initiate discussions around their work before integrating it with the rest of the codebase.
* Staging Area
  * One thing that sets Git apart from other tools is that it's possible to quickly stage some of your files and commit them without committing all of the files you have modified.
* No more single point of failure.
  * With SVN, if the central repository goes down or some code breaks the build then no other developers can commit their code until the repository is fixed. With Git, each developer has the own repository, so it doesn’t matter if the central repository is broken. Developers can continue to commit code locally until the central repository has been fixed, and then they can push their changes.
* It’s available offline.
  * Unlike SVN, Git can work offline, allowing your team to continue working without losing features if they lose connection.
* It’s faster to commit.
  * Because you commit to the central repository more often in SVN, network traffic slows everyone down. Whereas with Git, you’re working mostly on your local repository and only committing to the central repository every so often.

### community
* In many circles, Git has come to be the expected version control system for new projects. If your team is using Git, odds are you won’t have to train new hires on your workflow, because they’ll already be familiar with distributed development.

### human resources
* To a certain extent, your software development workflow determines who you hire. By choosing Git as your version control system, you’re making the decision to attract forward-looking developers.

### git via software as a service platforms
* provide added value features such as:
  * pull requests
  * issue tracking
* public code repositories
  * facilitate sharing and reuse
  * promote collaboration
  * public money, public code
  * GDS [Digital Service Standard](https://www.gov.uk/service-manual/service-standard) states (point #8): Make all new source code open

### not just for teams of coders
* ability to save a change with a note about what was changed and why, who made the change and when.
  * operation / data centre - scripts, configuration, documentation, on call manual, procedures.
  * business analysts - business requirements documentation.
  * testers - manual test documentation and test automation code.
  * service desk - FAQs and call workflow.

## clients
* [gitforwindows](https://gitforwindows.org/)
* [sublimemerge](https://www.sublimemerge.com/)


## links
* [git scm website](https://git-scm.com/)
* [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
* [why git](https://www.atlassian.com/git/tutorials/why-git)
* [From Collaborative Coding To Wedding Invitations: Github Is Going Mainstream](https://www.wired.com/2013/09/github-for-anything/)
* [2007 Tech Talk: Linus Torvalds on git](http://www.youtube.com/watch?v=4XpnKHJAok8)
* [Git for Humans Speakerdeck by Alice Bartlett](https://speakerdeck.com/alicebartlett/git-for-humans)
* [Git for Humans Gist by Lucio Martinez](https://gist.github.com/luciomartinez/11277737)
* [Knowledge is Power: Getting out of Trouble by Understanding Git - Steve Smith](https://www.youtube.com/watch?v=fHLcZGi3yMQ)
