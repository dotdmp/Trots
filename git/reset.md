
# git reset

The **git reset** command allows you to permanently delete the information about any changes and commits in the repository.

Let's say you have made some changes in your repository. And have executed some commands:
    
    $ git add .
    $ git commit -m 'Some changes'

The **git reset** command allows you to undo this commands and return the whole repository or a single file to it's previous state at any stage of the past.

**git reset is designed to undo local changes**

**Resetting completely removes a changeset**

>You should never use git reset when any snapshots after have been pushed to a public repository. After publishing a commit, you have to assume that other developers are reliant upon it.

## git log

In order to use git reset you have to get the **id** of the commit that you want to come back. You can obtain this information by calling:

    $ git log

It will show you the list of commits, it's authors, date and descriptions:

    commit 54b4128173bb244e6da8aa9fdd6afb93ea1f071f (origin/master)
    Author: USERNAME <USER@EMAIL>
    Date:   Tue Jan 22 04:13:04 2019 +0300

In this example *54b4128173bb244e6da8aa9fdd6afb93ea1f071f* is the commit id.

## git reset --hard

This command will undo all the changes made after a commit and revert the working directory to the state that it had just after the commit:
    
    $ git reset --hard 54b4128173bb244e6da8aa9fdd6afb93ea1f071f

It is the most powerful and also the most dangerous command of Git.

## get reset --mixed

Soft reset allows you to undo both **git commit** and **git add** operation. Working directory files are not affected. After mixed reset the repository will be reverted to the state where some changes in the working directory were made since a commit but **git add** and **git commit** commands were not called.
    
    $ git reset --mixed 54b4128173bb244e6da8aa9fdd6afb93ea1f071f

<s>$ git add .</s>

<s>$ git commit -m 'Some changes'</s>

## git reset --soft

Soft reset allows you to undo the **git commit** operation. After soft reset the repository will be reverted to the state where **git add** command was already called but **git commit** wasn't.

    $ git reset --soft 54b4128173bb244e6da8aa9fdd6afb93ea1f071f

After executing this command the system will be reverted to the state:
    
    $ git add .

<s>$ git commit -m 'Some changes'</s>

## How to cancel and undo the reset operation

After a reset commits can become '*orphaned*' which means there is no direct path to access them anymore. These *orphaned* commits can usually be found and restored using **git reflog**.

The information of all the commits that have been reset will be marked for deletion and will be destroyed by *git garbage coollector* which usually runs every 30 days.

## Read more

More detailed information about this command:

- [Reference](https://git-scm.com/docs/git-reset) : https://git-scm.com/docs/git-reset
- [Detailed description](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset) : https://www.atlassian.com/git/tutorials/undoing-changes/git-reset
