##02 - Getting Setup with Git

The whole purpose of Git is to take control of your projects source code and other files. 
The way we do this is by creating what is called a "code repository" or just "repo" that contains our code and
once we "initialise" this repository, Git will watch over it very carefully for any changes, additions and
deletions. 
By doing this Git can provide us with a history of everything that has taken place in the repo
and even allows us to go back to earlier versions should you ever need to. 
This becomes even more imortant when you have more than one person working on a project but for the
purpose of this course we will assume you are working by yourself and we won't get too bogged
down in the more specialised details.
Even with just the few commands we'll learn here you will have a very powerful source control system that
will keep your code and other files safe and available anywhere you can log in to a terminal.

###How it works
Typically you will have a repo online at a hosting service like GitHub or Bitbucket, these are usually
free for public repositories but if you need to keep your code private they provide this service for a small fee.
This is where you would typically store your code and is typically called the 'origin' and is where all
team members 'push' there changes to (this will make more sense shortly).
On your machine at home or at your office, you have a copy of this repo whcih you keep up to date by 'pull'-ing
changes from the origin (possibly made by other team members) and 'push'-ing any changes you may have made.

A typical work flow involves pulling the changes first thing before you start work on the project and then you might push
any changes during day or just once at the end. This way you always have an up to date copy on the server (GitHub say) 
and a copy on your local machine. 
This means you can also go home and download the project from the server and start work, this is called 'cloning'. 

Let's make this a bit more concrete.

###Create a GitHub repo
Head over to https://github.com and sign up for an account. Make sure you create a sensible username as it's very 
hard to change and doing so can screw up your whole repo in the future should you need to change it.

There is may ways to set up a project and repo but by far the easiest way is to create the repo at the 
origin (GitHub in this case) and 'clone' it to your local machine so go ahead and create a repo by going
to the Repositories link and selecting 'New'.
Again, choose a sensible name for the repo, especially if it's public so people can search for it easier (they may want
to help with your project!). For this tutorial name the repo `CLI-Calculator-Tutorial`.
Add a brief description and initialise it with the README file which should be filled out to provide a brief outline
of your project. You can also add a .gitignore file and a license, we'll cover the .gitignore file shortly.
Click Create repository and you're done, you should be able to navigate to it and see your repo with its README.md file.

###Clone your repo
Using the directory structure in the first tutorial for instance, open up Git Bash and navigate to the `tools` folder.
For those new to Bash you do this by entering the command like so:
`$ cd /c/Programming/C++/Projects/Tools/`
and you should now see your bash prompt display your username and this path indicating that you are at that folder location.

In this folder we will clone our new repo by entering the following:
`git clone <to repo link here>`
you can get the repo link from your online repo by selecting the 'Clone or download' button, the popup will have the URL
for you to copy.
If everything is setup ok you should now have a new folder under the Tools folder name after the repo which can open up
in your favourite editor or Visual Studio and start work.
