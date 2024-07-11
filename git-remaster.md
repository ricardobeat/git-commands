This doesn't work, git pull fails because of ff-only config in .gitconfig

    git pull origin $MAIN_BRANCH:$MAIN_BRANCH --rebase --autostash
    git rebase origin/$MAIN_BRANCH --rebase-merges --autostash

can't use `git rebase` directly from origin
can't use `git fetch branch:branch` as it doesn't take rebase arg

so the only solution is to stash manually before, as the script does.
