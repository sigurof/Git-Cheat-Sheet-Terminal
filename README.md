# Making a repository with existing code

I started to write this as a quick reference just for myself. For some reason, I fleshed it out much more than I needed to. I doubt this will be of use to anyone but it'll be a waste to delete the text now that it's written.

# With GitHub as remote:

Say you have existing code in a directory <code>somewhere/src/</code>

To make a remote on a github repository, go to github.com in your web browser and create a new repo there. Skip all optional things like initiating with a readme. Let's say you called it MyRepository. After creation, get the repository's URL by clicking the green "Clone or download" button in the browser. We'll refer to this URL as 'githuburl' without ''. Now, in the terminal type:

<code> user@src > git init</code>

This tells git to make a new repo (this does not affect already existing files, it just makes a .git/ directory which contains some files. You should not mess with these files if you don't know what you are doing). Currently, git thinks the new repository is empty. We need to register the new changes (which in this case is the existence of all your previous code and files in the directory):
  
<code> user@src > git add -A</code>

dash A for "all". Now that we have added all previously existing files, git is aware of these "changes" but still does not consider them to be in effect. To make it so, we type:

<code> user@src > git commit -m "Write commit message here" </code>

The commit message should give some details about the sort of changes you have made since the last time you commited. In this case, since we are committing an existing codebase, it's not very important what we write. Now we want to upload all the files in src/ to the remote repository on github.com. We use the url 'githuburl' that I talked about earlier, when we tell git that our repository has a remote origin on that location:

<code> user@src > git remote add origin githuburl</code>

To check that you typed the correct url, you can run the following, which will print the urls used for pushing and pulling.

<code> user@src > git remote -v </code>

Finally, we actually upload our files from src/ to github by 'pushing' the committed changes to the remote repository.

<code> user@src > git push origin master</code>

# With a directory on a computer or hard disc as the remote repository
Let the source directory = <code> /home/username/src/ </code>

Let the desired remote directory be <code> /remoteharddisc/dir/ </code>

<code> user@somewhere > cd /home/username/src/ </code>

<code> user@src > git init </code>

<code> user@src > git add -A </code>

<code> user@src > git commit -m "First commit"</code>

Now we have made a local git repo. We want to make a remote one now.

<code> user@src > cd /remoteharddisc/dir/ </code>

<code> user@dir > git clone --bare /home/username/src remote-codebase.git</code>

Now we can make changes in <code>/home/username/src/</code> and push them to the remote repository when we want.

# Making a new branch for local codebase and update the remote

<code> user@src > git branch newbranchname</code>
<code> user@src > git checkout newbranchname</code>
<code> user@src > git push remote-repo newbranchname</code>
