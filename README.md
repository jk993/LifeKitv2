## Our Work Flow

We will be following a model of forks and branches. We each work on our own fork, and only Mark (who's managing operations) can merge to the master repo. If your git-fu fails you and everything is completely messed up, it won't affect anyone else this way, and you can always do a clean pull from master to reset everything.

### First Steps

1. Click the button at the top of this repository that says "Fork". This will create your own personal fork where your (or our) git-fu failures are insulated away from the rest of the team. You'll notice the repository URL is your repo's copy of my master repo so use this information to check your commands in the following steps
1. Clone your personal fork to your programming device (hopefully a real computer of some sort and not like a phone). On the commandline (which I'm going to assume you're using), this is `git clone (link to your forked repo). It may ask for credentials or other info and it's up to you to decide if/how to handle that.
1. Add upstream as a remote target (aka you can push/pull to it). The main repository will be called "upstream" and is added to your environment using `git remote add upstream (link of where you forked from (Khoi's Repo of LifeKitv2) **REMEMBER, NEVER EVER EVER DO SOMETHING THAT LOOKS LIKE `push upstream`**
1. Your evironment should now be set up and ready to use

### Basic Flow

I'm assuming some special cases here, chances are you can skip some of these steps (but they're all harmless in any case if you do a step you didn't have to).

1. Ensure you're up to date with upstream/master
	1. Checkout master: `git checkout master`
	1. Pull upstream: `git pull upstream master`
	1. Update your fork: `git push origin master`
1. Put yourself on a branch other than master
	1. If you need to make a new branch
		1. Create a branch: `git branch <name-of-branch>`. *Please use dashes instead of spaces because we're working on the commandline and nobody wants to re-learn why bash and quotes don't mix*
		1. Checkout that branch: `git checkout <name-of-branch>`
	1. If the branch already exists:
		1. Checkout that branch: `git checkout <name-of-branch>`
		1. Make sure you're up to date: `git rebase master`
		1. If the rebase said anything other than "`Current branch <name-of-branch> is up to date.`" then push to your fork: `git push origin <name-of-branch>`
		1. If git complains about something (just trust me on this one): `git push origin <name-of-branch> -f`
1. Actual coding work!
	1. Write some code until you feel the need to commit (remember this is all local to you, so commit as often as possible because it won't affect anyone else)
	1. Stage your changes: `git add -A`
	1. Commit your changes: `git commit -m "some useful commit message"`
	1. Push your changes: `git push origin <name-of-branch>`
	1. Keep on coding until you've completed somethng big enough that other people need to look at it
1. PR: Pull Request / Peer Review
	1. If you made way too many commits and it's confusing use `git rebase -i HEAD~20`. Be careful because you're rewriting history a bit here and can ruin your fork very quickly. Use `git log` to check that the result makes sense
	1. When you're ready for review, log onto [GitHub](https://github.com/) (hint: you're probably already here)
	1. Go to the [upstream project page](where you forked from (Khoi's Repo of LifeKitv2))
	1. You should see a button at the top with your branch saying "Compare & Pull Request". Click that
	1. Create a pull request with information about your commit. Please add in-line comments if things are confusing (though that should warrant code comments anyway)
	1. If/when it's set up, CI should automatically test your PR and reject you if it's failing the tests
	1. If you need to change something, you should still be able to push to that same branch in your fork and the PR will update, and CI should re-test your new code.
	1. When you have a :+1: from two other group members, merge the PR by clicking the button at the bottom of the page.
