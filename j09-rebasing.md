---
layout: page
title: Version Control with Git
subtitle: Updating a forked project
minutes: 25
---

The collaboration scenario we just went over is very neat, but it makes several assumptions that aren't always true. The biggest assumption is that only one person is working on a project at any given time. What happens if the person you're collaborating with makes significant changes of their own in the time while you're working on it. Your code might still work, but how do you update your project to include both your and their changes, and then include this in the pull request you send to them later?

This workflow is slightly more complicated, and involves "rebasing" your code on the latest version of their project. This is best explained with an example.

Let's pretend that your name is Angela and are collaborating on a project with someone named Ted. Ted is the owner of a repository, and you (Angela) have forked it and made a few really awesome changes in commits D, E, and F. Unfortunately, Ted has also made a few changes (commits A, B, and C), and you're not sure whether or not they will work with your changes. So you want to update it so that your changes are actually on "top" of his updated version.

The current situation:

```
fork --- A --- B --- C (Ted)
    \
     D --- E --- F (Angela)
```

What you (Angela) want:

```
fork --- A --- B --- C (Ted)
                      \
                       D --- E --- F (Angela)
```

The second scenario (what we want) is much nicer, as Angela is now in a position to send a pull request to Ted. We have the most up-to-date version of the code will *all* changes, so we can make sure they play nice with each other. Let's try doing this for real with your partner's repository.

Let's clone our forked copy of your partner's planets repository from GitHub, and make a file called `jupiter.txt`. Add whatever you want to it, then commit it.

```{.bash}
git clone https://github.com/yourName/planets-partnersName.git
cd planets-partnersName
echo 'jupiter is big' > jupiter.txt
git add .
git commit -m 'added jupiter'
# you can push it if you want to, but it doesn't matter for this example
```

Now let's give our partner some changes they have to deal with. In your copy of `planets` (`planets-yourName`), make a file called `saturn.txt`, and add whatever you want to it. Commit that too, then push it to GitHub.

```{.bash}
cd ../planets-yourName
echo 'saturn is the prettiest planet' > saturn.txt
git add .
git commit -m 'added saturn'
git push origin master
```

`cd` back to your fork of your partner's project. So right now, this is the current situation:

```
fork --- added saturn (partner)
   \
    added jupiter (us)
```

What we want to do is this:

```
fork --- added saturn (partner)
                \
                 added jupiter (us)
```

We 
