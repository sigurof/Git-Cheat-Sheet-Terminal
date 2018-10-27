# How-To-Use-Git-Memo

# With GitHub as remote:

Say you have existing code in a directory <code>somewhere/src/</code>

To make a remote on a github repository, go to github.com in your web browser and create a new repo there. Skip all optional things like initiating with a readme. Let's say you called it MyRepository. After creation, get the repository's URL by clicking the green "Clone or download" button in the browser. We'll refer to this URL as 'githuburl' without ''. Now, in the terminal type:

<code> user@src > git init</code>

This tells git to make a new repo (this does not affect already existing files, it just makes a .git/ directory which contains some files. You should not mess with these files if you don't know what you are doing). Currently, git thinks the new repository is empty. We need to register the new changes (which in this case is the existence of all your previous code and files in the directory):
  
<code> user@src > git add -A</code>

dash A for "all". Now that we have added all previously existing files, git is aware of them but still does not consider them to be in effect. To make it so, we type:

<code> user@src > git commit -m "Write commit message here" </code>

The commit message should give some details about the sort of changes you have made since the last time you commited. In this case, since we are committing an existing codebase, it's not very important what we write. Now we want to upload all the files in src/ to the remote repository on github.com. We use the url 'githuburl' that I talked about earlier, when we tell git that our repository has a remote origin on that location:

<code> user@src > git remote add origin githuburl</code>

Now we can check that the url was set correctly by typing the following and checking if the url is the same as what you typed in.

<code> user@src > git remote -v </code>

Finally, we actually upload our files from src/ to github by 'pushing' the committed changes to the remote repository.

<code> user@src > git push origin master</code>


  
  
