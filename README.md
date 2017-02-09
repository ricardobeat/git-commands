
# git-commands

A collection of useful git commands.

## Installation

    git clone https://github.com/ricardobeat/git-commands ~/.git-commands

    echo export PATH="~/.git-commands:$PATH" > ~/.profile

### `git author-stats [author]`

Output number of lines added / removed by `author`

    ★ git author-stats Pietro
    Added: 116461, removed: 80818, total: 35643, modified: 197279 lines

### `git delete-merged-branches`

Delete all branches that have already been merged into master.

### `git-dig [string]`

Search for commits that include `string` in their change set.

### `git-find [search strings]`

Find files containing the search strings, in any order. For example:

    ★ git find modules main modal js
    main/lib/modules/modal/index.js

### `git-grep-rank [string]`

Display authors of files containing `string`, ranked by frequency.

    homebrew-core ★ git grep-rank dumb
    10 matches for 'dumb'
       5 s172262
       3 Dominyk Tiller
       1 Zhiming Wang
       1 Fred McCann
       1 David Holm

### `git-open`

Simultaneously open all changed files using `$EDITOR`, according to `git status`. Lets you pick up 
work in progress without depending on editor 'projects' state.

### `git-rank`

Display ranking of authors by number of commits + extra stats.

![git-rank](https://cloud.githubusercontent.com/assets/97396/22784387/1e237d4e-eed0-11e6-9527-16c3e79e1158.png)

### `git-remaster`

While working in a branch, `fetch` latest `master`, then rebase current branch on top of that. Use 
to keep in sync with main development branch.

### `git-repush`

Delete remote branch, then push again. To work around `-f` restrictions. Bails out if branch name is
`master` or `trunk`.

### `git-shower`

Run GC + prune. Optimized for a huge (~100k files) repository, might not work for you.

### `git-size [commit]`

Show the size in bytes introduced (or removed) by a specific commit. Accepts any ref identifier 
that git understands: hashes, `HEAD^`, etc.

### `git-snapshot [note]`

Create a named stash, including an optional text note. This will *not* be featured in the stash list,
only in reflog (and will be GCed at some point). Use as safety checkpoints while furiously changing code.

### `git-sort [hashes]`

Sort a list of SHA1 commit hashes by their ordering in the history. Defaults to looking at the past 1000 commits,
can be overriden by setting the `N` environment var.

    git sort 2d5cbab63ba cf39029de04 61bdf05bbc1
    cf39029de04
    61bdf05bbc1
    2d5cbab63ba

    cat shas.txt | git sort
    cf39029de04
    61bdf05bbc1
    ...

### `git-stash-merge`

Commands like `git stash pop` will refuse to apply over a dirty tree, even when an automatic merge is possible.
The `stash-merge` command will create a new stash object from your state and try to `merge` them together.
In chase the the merge fails you still have both in stash list.

