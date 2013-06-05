---
layout: post
title: You CAN see staged diffs
tags: git
---
## git diff --staged is awesome

Up until recently I'd never bothered to seek a way to look at the
diffs of staged files.
The default method will produce a diff assuming a file is not staged for commit:

{% highlight bash %}

git diff file1.txt

{% endhighlight %}

However, if file1.txt *is* staged for commit, the same command displays nothing.

{% highlight bash %}
git add file1.txt
git diff --staged file1.txt
{% endhighlight %}

Where this *really* becomes handy is when you've only staged part of a file for commit.

{% highlight bash %}

git add -p file1.txt
# Select only one or two changes among possibly many
git diff --staged
# Enjoy seeing only what you staged.

{% endhighlight %}

Enjoy :)
