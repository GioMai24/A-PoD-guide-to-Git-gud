# <p align='center'> Why does git fail me? </p>
It doesn't, you are the failure.

If you struggle with git it means you are treating git commands as magical invocations that sometimes go awry. There is only one spellbook that will save you: **THE DOCUMENTATION**.

Nonetheless the following is a simple start to do some magic. You will want to go and **READ THE DOCUMENTATION** of the few commands mentioned here to truly unlock their power, and be able to gaslight your friends into believing you're their only git asset.

## <p align='center'> Setup and SSH </p>
I love ssh, and git comes with a whole **DOCUMENTATION** section about it: [SSH setup](https://docs.github.com/en/authentication/connecting-to-github-with-ssh). Carefully read through it following instructions. We do like instructions. When you are done, you will be automagically able to access your github online stuff from your terminal without tokens or passwords.

You can easily get repos' files on your local machine by copying the ssh link on the green "code" button inside the main repo page, and doing `git clone [LINK]` in your terminal. This will create a new directory named as the repo in your current directory. You can freely move it and rename it, the heart of the repo resides in the `.git`[^2] directory inside it. If you remove the latter you will kill the connection to git, leaving you with a regular directory and all the files inside it. Of course if you clone someone else's repo you won't be able to push your changes to it, only to get updates. That's why forks exist.
[^2]: Files starting with a `.` are hidden files. They can be shown by `ls -a`.

## <p align='center'> What the fork? </p>
A fork is a copy of someone's repo. Pretty simple. You can sync it to keep it updated, you can tinker stuff without bothering the original creator, and you can bother the original creator by doing pull requests. A pull request is non other than asking the creator of the repo to pull your modifications to his repo. Very different from pulling his updates to your fork.

I find it useful to create a branch in the forked repo. This allows you to update the main branch as the creator updates it (say, with weekly exercises), and modify stuff on your own branch.

## <p align='center'> Branch republic </p>
ALWAYS CHECK WHERE YOU ARE WORKING. You can do so by issuing `git branch`. This is a useful command which also lets you create new branches by simply adding a name: `git branch [NAME]`. If you want to switch branches, well... `git switch [NAME]` to it.

See? Git is very simple. Very intuitive[^3].
[^3]: may God have mercy if you ever have to `git rebase` something.

Sometimes you may want to take a file from another branch: `git restore --source other-branch -- path/to/your/file.txt` should do the work[^4].
[^4]: I haven't tested this yet, I used to use `git checkout`, but it looks like it's been splitted in `git switch` and `git restore`.

## <p align='center'> Update </p>
To gather possible updates you first want to `git fetch` them (on the appropriate branch), and then `git merge` the changes in your branch. Git people are so lazy that they created `git pull` to do the two operations together (which will not issue an actual pull request: you're pulling stuff, not asking your stuff to be pulled).

## <p align='center'> The Holy Trinity: Add Commit Push </p>
After hours of vibe coding you need to push your changes online. How? With three simple commands:
- `git add [PATHS]`: tell git which files have been added or modified since your last commit. `git add .` will git add the content of the current directory.
- `git commit -m "WHAT HAVE YOU DONE?"`: commit the added files to be pushed, along with a simple comment (mind: it will be shown to everyone).
- `git push`: officially send the changes online.

Listen, no one cares about your `.ipynb_chekpoints/` or `__pycache__/` directories, don't push useless stuff on git. You can easily ignore stuff by creating a `.gitignore` text file with all the paths `git add` shall ignore. I find it funny that `.gitignore` is also git added and pushed -- it might even be useful sometimes -- but if you prefer to silently ignore your `homework/` directory you can also edit the `.git/info/exclude` file in the same way. You wouldn't think there was much else to say about this, instead there is **DOCUMENTATION** about this too! And it actually suggests pretty things to do.

Finally, use `git mv` and `git rm` if you want to move, rename, or remove files that have been git added.
