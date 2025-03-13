Work in progress. I am shortening the text..

# Git-Bash
Commands from GitHub for dummies book

Chapter 1
Understanding the Git in GitHub

$ git --version
git version 2.37.2.windows.2

To create a new folder called gitpractice.
$ cd ~/Desktop
$ mkdir git-practice
$ cd git-practice

You can update all Git repositories to use “main” as the primary branch name
with this command:
$ git config --global init.defaultBranch main

Run this config command before you initialize your Git
repository so that your primary branch is called main.
Now, you can tell Git to track this folder using the init command.
$ git init
Initialized empty Git repository in /Users/drguthals/Desktop/
git-practice

Make sure that you have a clean folder. You can check with the status
command:
$ git status
On branch main
No commits yet
nothing to commit (create/copy files and use "git add" to track)
$

Then, you can create a file to have Git start tracking and confirm the file is in the
folder:
$ echo "practicing git" > file.txt
$ ls
file.txt
$

On Windows, you can open this folder with the explorer <path> command:
$ explorer .

This puts . as the <path> for each command. The period (.) tells the terminal to
open the current folder. You could also use a different path with these commands
to open other folders.
After the folder is open, double-click the file called file.txt, and the file opens
with TextEdit on Mac, gedit on Linux, and Notepad on Windows. You can see that
the words “practicing git” are actually there.
Close the file. Now, you can tell Git that you want to save this as a particular
version. Back in the terminal:
$ git add file.txt
$ git commit -m "Adding my file to this version"
[main (root-commit) 8d28a21] Adding my file to this version
1 file changed, 1 insertion(+)
Create mode 100644 file.txt
$ git status
On branch main
nothing to commit, working tree clean
$
You can make a change to your file in the text file. Open the file again, change the
text to say “Hi! I’m practicing git today!” and then choose File ➪ Save and close
the text application.
When you go back to the Terminal to check the status of your project again, you
should see that Git has noticed that the file has changed:

$ git status
On branch main
Changed not staged for commit:
(use "git add <file..." to update what will be committed)
{use "git checkout -- <file>..." to discard changed in working directory)

modified: file.txt
no changed added to commit (use "git add" and/or "git commit -a")
$
Commit this version of your file again and notice that Git recognizes that everything
has been saved to a new version:

$ git add file.txt
$ git commit -m "I changed the text"
[main 6d80a2a] I changed the text
1 file changed, 1 insertion(+), 1 deletion(-)
$ git status
On branch main
nothing to commit, working tree clean
$
If your terminal starts to get too cluttered, you can type clear to clear some space
and make it more visually appealing. Don’t worry; you can always scroll up and
see everything you typed earlier!

Say that you actually want to see the original change, when you added “practicing
git”. First, get the log of all the commits you have made:
$ git log
commit 6d80a2ab7382c4d308de74c25669f16d1407372d (HEAD -> main)
Author: drguthals <sarah@guthals.com>
Date: Sun Aug 7 08:54:11 2022 -0800
I changed the text
commit 8d28a21f71ec5657a2f5421e03faad307d9eec6f
Author: drguthals <sarah@guthals.com>
Date: Sun Aug 7 08:48:01 2022 -0800
Adding my file to this version
$
Then ask Git to show you the first commit you made (the bottom most one). Make
sure that you’re typing your unique commit hash. In this book, the hash starts
with 8d28a2. Make sure you type the entire hash that appears in your Git log.


Instead of typing the entire hash (and possibly having a typo), you can highlight
the hash with your mouse, right-click and choose Copy, and then after git
checkout, you can right-click and choose Paste. Using the keyboard shortcuts
Ctrl+C or ⌘ -C doesn’t work.
$ git show 8d28a21f71ec5657a2f5421e03faad307d9eec6f
commit 8d28a21f71ec6567a2f5421e03faad307d9eec6f

Author: drguthals <sarah@guthals.com>
Date: Sun Aug 7 08:48:01 2022 -0800
Adding my file to this version
diff --git a/file.txt b/file.txt
new file mode 100644
index 0000000..849a4c7
--- /dev/null
+++ b/file.txt
@@ -0,0 +1 @@
+practicing git
$
You can see that practicing git was added to the file in that original commit.
For more information on how to use Git on the command line, check out the
following resources:
»»The GitHub Git Cheat Sheet at https://education.github.com/git-cheatsheet-
education.pdf
»»The Visual Git Cheat Sheet at http://ndpsoftware.com/git-cheatsheet.
html
»»The Git Docs page at https://git-scm.com/doc
Another resource for learning and understanding Git is https://learngit
branching.js.org. This is a good self-guided set of exercises.

Chapter 2
Setting Up Your
Collaborative
Coding Environment

Chapter 3
Introducing GitHub
Repositories

Chapter 4
Setting Up a GitHub
Website Repo

Chapter 5
Creating a Website
with GitHub Pages

Then, open the index.md file and change the code to include sections. For example,
my code looks like this:
# My Projects
Here is a list of projects that I am working on:
# My Interests
I'm interested in teaching novice coders about computer science!
# My Blog

I'm really excited to blog my journey on GitHub.com.
# Get in Touch
<ul>
<li><a href="https://twitter.com/{{ site.twitter_username
}}">Twitter</a></li>
<li><a href="https://github.com/{{ site.github_username
}}">GitHub</a></li>
</ul>
Save, stage, commit, and push your changes to your branch and then create and
merge the pull request into the main branch. After a couple of minutes, refresh the
website page to see your changes.

Creating a blog
First, create a new folder called _layouts and create a file within that folder called
post.html. The _layout/post.html file should contain the following code to
create a blog-style:
layout: default
<h1>{{ page.title }}</h1><p>{{ page.date | date_to_string }} –
{{ page.author }}</p>
{{ content }}

Then, create a new folder called _posts and a file inside with the date and a title.
Typically, blog posts are made with YEAR-MONTH-DAY-TITLE.md. For example, this
code is in a file called _posts/2019-01-01-new-year.md:
---
layout: post

author: sguthals
---
Write your blog post here.
Finally, in your index.md file, add the following code below the My Blog section:
<ul>
{% for post in site.posts %}
<li>
<a href="{{ post.url }}">{{ post.title }}</a>
</li>
{% endfor %}
</ul>
Save, stage, commit, and push your changes to your branch and then create and
merge the pull request into the main branch. After a couple of minutes, refresh the
website page to see your changes.

Linking project repos
You can link GitHub project repos to your website in the same way you link social
media, described in the section “Adding sections to your website,” earlier in this
chapter. Putting a link directly to a repo can be efficient. However, you can also
create web pages for project repos as well, as described in Chapter 4.
Open the index.md file and add the following code, replacing the URLs with links
to projects you’re the author of. This code shows linking to a project repo web
page and directly to a project repo:
<ul>
<li><a href="https://sarah-wecan.github.io/HelloWorld/">Hello
World Project</a></li>
<li><a href="https://github.com/thewecanzone/GitHubForDummies
Readers">GitHub For Dummies Repo</a></li>
</ul>

Chapter 6
Forking GitHub
Repositories

Cloning a Repository
After you have a repository cloned on your local computer, you can view and
modify metadata about it in your terminal. Open the terminal and go to a directory
where you have a GitHub repository. If you need an example, clone https://
github.com/thewecanzone/GitHubForDummiesReaders by typing
$ git clone https://github.com/thewecanzone/
GitHubForDummiesReaders
Cloning into 'GitHubForDummiesReaders'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.

remote: Compressing objects: 100% (15/15), done.
remote: Total 15 (delta 4), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (15/15), done.
$ cd GitHubForDummiesReaders
You can verify where the remote/target repo is with the following command:
$ git remote -v
originhttps://github.com/thewecanzone/GitHubForDummiesReaders.
git (fetch)
originhttps://github.com/thewecanzone/GitHubForDummiesReaders.
git (push)
If you cloned the same repo as I did, you see the exact same origin URLs for fetch
and push. You should see that the remote repo is one owned by thewecanzone and
not dra-sarah. Alternatively, if you run the same command on a repo that you
own, you should see your username. For example, if I run the command in the
directory where I cloned my website repo that I created in Chapter 4, I would see
$ git remote -v
originhttps://github.com/dra-sarah/dra-sarah.github.io.git (fetch)
originhttps://github.com/dra-sarah/dra-sarah.github.io.git (push)

If you try using the command on a Git repo that doesn’t have a remote origin
(meaning it isn’t hosted on GitHub.com or any other remote place), you simply
won’t get any information back. For example, in Chapter 1, I created a simple Git
repo called git-practice. Running the command in that directory gives you
nothing back:
$ git remote -v

If you clone the repo using the command line, you may want to set the upstream
remote, which I explain in the section “Getting unstuck when cloning without
forking,” later in this chapter. You can see both the forked remote origin and
original remote upstream if you run the git remote -v command in the directory
where you cloned the repo:
$ git remote -v
originhttps://github.com/dra-sarah/GitHubForDummiesReaders.git
(fetch)
originhttps://github.com/dra-sarah/GitHubForDummiesReaders.git
(push)
upstreamhttps://github.com/thewecanzone/GitHubForDummiesReaders.
git (fetch)
upstreamhttps://github.com/thewecanzone/GitHubForDummiesReaders.
git (push)

Fetching changes from upstream

If you find yourself in a situation where you need to get the change from the
upstream, original repo, you can go to the directory where your forked repo is
and type
$ git fetch upstream
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/thewecanzone/GitHubForDummiesReaders
8404f3b..e02a4d2 master -> upstream/master
$ git checkout -b new-branch
Switched to a new branch 'new-branch'
$ git merge upstream/master
Updating 8404f3b..e02a4d2
Fast-forward
README.md | 2 +-
1 file changed, 1 insertion(+), 1 deletion(-)

These three commands fetch the changes from the upstream repo, ensure that
you’re on your local, forked repo on a new branch, and then merges the changes
from the upstream repo into your forked repo.

Getting unstuck when cloning
without forking
One common problem people run into is they forget to fork a repository before
they try to contribute to it. The following scenario describes one example of
getting into this situation.
Here’s the scenario: You clone a repository onto your local computer, modify the
code, commit changes to main, and are ready to push your changes. But then
you get a scary-looking error message. You may get the message in VS Code (see
Figure 6-8), GitHub Desktop (see Figure 6-9), or in the terminal:

$ git push origin main
remote: Permission to thewecanzone/GitHubForDummiesReaders.git
denied to dra-sarah.
fatal: unable to access 'https://github.com/thewecanzone/
GitHubForDummiesReaders.git/': The requested URL returned
error: 403

The error message tells you that you don’t have permission to push to this repository.
You should have forked the repository first. You also made the mistake of
committing directly to the development branch. As I recommend elsewhere in the
book, it’s a good practice to make all your changes in a temporary branch; this
applies to any protected branches such as main or development.

1. Migrate your changes to a new branch.
Right when you discover you’re targeting the incorrect remote repository, you
should move your changes to a new branch. You don’t want to accidentally pull
in changes from the upstream, original branch onto all the hard work you just
finished. This step can get tricky, but luckily there’s a Git alias to help. See the
nearby sidebar “Creating a Git Alias” for help. After you have the git migrate
alias, go to the directory where your repo is in your terminal and type
$ git migrate new-branch
Switched to a new branch 'new-branch'
Branch 'main' set up to track remote branch 'main' from
'origin'.
Current branch new-branch is up to date.
Confirm that the new branch has been created:
$ git status
On branch new-branch
nothing to commit, working tree clean
You can also confirm that your commits are only in this new branch and
no longer in the old branch by running a log command to compare the
two branches:
$ git log main..new-branch --oneline

This lists the commits in new-branch that are not in main. The --oneline flag
prints each commit on a single line, which is useful when you just need a
summary of commits and not the full details.
2. Set the upstream remote to be the original GitHubForDummiesReaders
repo.
To add an upstream remote to your repo, go to the terminal and type
$ git remote add upstream https://github.com/thewecanzone/
GitHubForDummiesReaders.git

Confirm that the upstream remote was added correctly:
$ git remote -v
originhttps://github.com/thewecanzone/
GitHubForDummiesReaders.git (fetch)
originhttps://github.com/thewecanzone/
GitHubForDummiesReaders.git (push)
upstreamhttps://github.com/thewecanzone/
GitHubForDummiesReaders.git (fetch)
upstreamhttps://github.com/thewecanzone/
GitHubForDummiesReaders.git (push)
3. Fork the repo.
Back on GitHub.com, go to the original repo and click Fork at the top right of
the repo home page. The page refreshes, and you see your own version of the
repo, referencing the original repo (refer to Figure 6-2).
4. Set the origin remote to be your forked repo.
After you have your own fork of the repo, you can change your remote origin
to be your version:
$ git remote set-url origin https://github.com/dra-sarah/
GitHubForDummiesReaders.git

3. Fork the repo.
Back on GitHub.com, go to the original repo and click Fork at the top right of
the repo home page. The page refreshes, and you see your own version of the
repo, referencing the original repo (refer to Figure 6-2).
4. Set the origin remote to be your forked repo.
After you have your own fork of the repo, you can change your remote origin
to be your version:
$ git remote set-url origin https://github.com/dra-sarah/
GitHubForDummiesReaders.git
You can also confirm that all your remote URLs are correctly set:
$ git remote -v
originhttps://github.com/dra-sarah/GitHubForDummiesReaders.
git (fetch)
originhttps://github.com/dra-sarah/GitHubForDummiesReaders.
git (push)
upstreamhttps://github.com/dra-sarah/GitHubForDummiesReaders.
git (fetch)
upstreamhttps://github.com/dra-sarah/GitHubForDummiesReaders.
git (push)

5. Push your branch to your forked version.
You’re now in the same state that you would be in had you forked the repo
before cloning. Back in VS Code, you can publish your branch.
6. Create a pull request.
Your forked repo detects a new branch and offers to have you create a pull
request (refer to Figure 6-4).

Chapter 7
Writing and
Committing Code

1. Open the terminal on your computer.
If you don’t know how to do so, see Chapter 1 for guidance.
2. Go to the directory where you want your project folder to be stored and
type the following commands:
$ git init best-example
$ cd best-example
The first command creates an empty Git repository in the specified directory,
best-example. Because the best-example directory doesn’t already exist,
Git creates it. The second command changes the current directory to this new
directory.

Writing Code
After you’re in a Git repository directory, you can start adding files. (If you aren’t
in a directory, see the previous section, “Creating a Repository” where I created
the best-example directory.)
For this example, you create three files by typing the following code:
$ touch README.md
$ touch index.html
$ mkdir js
$ touch js/script.js


Open the README.md in the editor by clicking in the file tree in VS Code. Then add
some Markdown relevant to your project. In this example, add the following text:
# The Best Example Ever
Which will be a part of the best commit ever.
Then add the following code to index.html.
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>It is the cod3z</title>
<script src="js/script.js"></script>
</head>
<body>
<h1>The Best Cod3z!</h1>
</body>
</html>

This HTML file references script.js. Open script.js in VS Code and add the
following code.
document.addEventListener(
"DOMContentLoaded",
function(event) {
alert('The page is loaded and the script ran!')
}
);
Make sure to save your changes to each file. Now test the code by opening index.
html in your browser from the terminal.
$ open index.html
The page loads in your default browser, and the alert message, shown in Figure 7-1,
appears.

Creating a Commit

Start by staging the README.md file:
$ git add README.md

The README.md file is added to the Git index. The Git index is the staging area for
creating commits to the repository. You can check the status of the repository to
see that the file has been added to the index:
$ git status
On branch main
No commits yet
Changes to be committed:
(use "git rm --cached <file>..." to unstage)
new file: README.md
Untracked files:
(use "git add <file>..." to include in what will be committed)
index.html
js/

As you can see, the README.md file is staged for commit. Meanwhile, the index.
html and js/ directory aren't yet tracked by this repository.
Why isn’t script.js listed in the untracked files section? Git is taking a shortcut
here. It notices that no files within the js/ directory are tracked, so it can simply
list the directory rather than list every file in the directory. In a larger code base,
you'll be glad Git isn’t listing every file in every subdirectory.

Committing a file
After you stage changes (see preceding section), you can create a commit. In this
example, I use the -m flag with the git commit command to specify a short commit
message. The following commands demonstrate how to create a commit and
specify the commit message in one step:
$ git commit -m "Add a descriptive README file"
[main (root-commit) 8436866] Add a descriptive README file
1 file changed, 3 insertions(+), 0 deletions(-)
create mode 100644 README.md
The file is committed. If you run the git status command again, you see that you
still have untracked files. The git commit command commits only the changes
that are staged.

Committing multiple files
After you commit the first file, you're ready to stage the rest of the files for a
commit.

$ git add -A
$ git status
On branch main
Changes to be committed:
(use "git reset HEAD <file>..." to unstage)
new file: index.html
new file: js/scripts.js
The -A flag indicates that you want to add all changes in the working directory to
the Git index. When you run the git status command, you can see that you've
staged two files.
When the js directory is untracked, git status lists only the js directory and none
of the files in the directory. Now that you're trying to stage the js directory, Git
lists the file in the js directory. Why the discrepancy? Git doesn't actually track
directories. It tracks only files. Therefore, when you add a directory to a Git repository,
it needs to add each file to the index.
Sometimes you need to write a more detailed commit message. In this example,
I didn’t specify a commit message when I run the commit command because
I plan to write a more detailed commit message:
$ git commit

If you don’t specify a commit message using the -m flag, Git launches an editor to
create a commit message. If you haven’t configured an editor with Git, it uses the
system default editor, typically VI or VIM.
There are legions of jokes about how difficult it is to exit VIM, so I won’t rehash
them all here. I’ll simply take a moment of silence in remembrance for friends
still stuck in the VIM editor.
For the record, to exit VIM, press the ESC key to exit the edit mode and type :wq to
exit and save or :q! to exit without saving.
To change the default editor to something like VS Code, run the following command
in the terminal:
git config --global core.editor "code --wait"

Committing Code with GitHub Desktop

Tracking a repository in Desktop
To install the command line tool on a Mac:
1. Make sure Desktop is the active application and then, in the application
menu bar, choose GitHub Desktop ➪ Install Command Line Tool.
2. From the terminal, make sure that you’re in the repository you want
Desktop to track.
For this example, I’m in the best-example.
3. Run the following command:
$ github .
The . in the command represents the current directory. It could, instead, be a
fully qualified path to a directory. GitHub Desktop launches (if it's not already
running) and opens the specified directory. Because the current directory is
already a Git repository, Desktop adds it to the list of repositories that it tracks.
It then sets this repository as the current repository so that you can browse the
repository’s history, switch branches, and create commits, as shown in
Figure 7-3

Publishing a repository in Desktop
1. Clicking the Publish repository button.
A dialog box to publish the repository appears (see Figure 7-4).
2. Fill in the details and click the Publish Repository button.
The repository is created on your GitHub.com account.


Committing in Desktop
Desktop is used only for Git operations. To edit the files in the repository, you still
need to use your editor of choice.
Make some changes so you have something to commit. In the example for this
chapter, you can make some changes to index.html shown in bold.
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>The Best Example</title>
<script src="js/script.js"></script>
</head>
<body>
<h1>The Best Cod3z!</h1>
<div id="message"></div>
</body>
</html>

Update script.js to populate the new DIV element, like civilized people would,
rather than use an alert message. Changes are in bold:
document.addEventListener(
"DOMContentLoaded",
function(event) {
var message = document.getElementById('message')
message.innerText = 'The script ran!'
}
);
Switch back to Desktop and click the Changes tab, shown in Figure 7-5.

Using GitHub Conventions
in Commit MessagesUsing GitHub Conventions
in Commit Messages

Emojis
Emojis are

Issue references

To reference an issue in a commit message:
1. In the commit description field, type Fixes #.
A few recent issues appear. If you don't see the issue you want to reference
and you don’t remember the issue number, you can start typing a word that’s
in the issue that you remember. For example, when I type # greetings an issue
pops up (see Figure 7-9).
2. Select the issue you want to reference and press Tab.
In this example, I selected issue 15. Desktop replaces #greetings with #15.

Chapter 8
Working with Pull
Requests

