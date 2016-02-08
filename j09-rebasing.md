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

Let's do this with our partner's repository.
