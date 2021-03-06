## Updating your project with our changes

Save all files you have open in an editor. Check if you have any uncommitted changes:

~~~{.sh}
git status
~~~

If it says `nothing to commit`, then you don't need to do a commit.  If it says
`Changes not staged for commit`, then you need to commit your changes:

~~~{.sh}
git commit -a -m "describe your changes here"
~~~

Next, you need to pull our changes to your local git repository. To do this, first add our github repository as a git remote:

~~~{.sh}
git remote add upstream https://github.com/iloveponies/<current-chapter>.git
~~~

Make sure to use the correct chapters repository! Now we can pull the changes into the local repository:

~~~{.sh}
git pull upstream master
~~~

If all went fine, an editor will open with an autogenerated merge-commit
message. Save and close this file (if this opened Vim for you and you're not
familiar with it, you can save and exit by typing `:x` and pressing enter).

If you got a merge conflict, you need to do the following:

<ul>
<li>
First, check which files have conflicts:

~~~{.sh}
git status
~~~
</li>

<li>
For each `file` listed under `Unmerged paths`, do the following unless the
`file` is under `src`:

~~~{.sh}
git checkout --theirs file
~~~
</li>

<li>
And the following for the files under `src` (if any):

~~~{.sh}
git checkout --ours file
~~~
</li>

<li>
Finally, commit this merge:

~~~{.sh}
git commit -a -m "merged upstream"
~~~
</li>
</ul>

Now your local repository has been updated. To update your remote github
repository as well, run:

~~~{.sh}
git push
~~~

And you are done.

### If all else fails, clone again

If you encountered some problems that you couldn't fix during the previous
steps, you can always clone you github repository again. First rename your old
clone, then clone again. As the first thing in the new clone, add our github
repository as a remote like before:

~~~{.sh}
git remote add upstream https://github.com/iloveponies/<current-chapter>.git
~~~

Make sure you have a copy of your answers to the exercises somewhere else!
Then run the following:

~~~{.sh}
git fetch upstream
git reset --hard upstream/master
git push --force
~~~

After this, you can copy your answers into this repository and continue working
in here.

