---
layout: post
title: You CAN see staged diffs
tags: git
---
Up until recently I'd never bothered to seek a way to look at the
diffs of staged files.
The default method will produce a diff assuming a file is not staged for commit:

{% highlight ruby %}
$ cat > file1.txt<<EOF
this is a file
it has lines
EOF
$ git add file1.txt
$ git diff file1.txt
# Empty!
$ git commit -m "First commit"
{% endhighlight %}

However, if file1.txt *is* staged for commit, the same command displays nothing.

{% highlight bash %}
cat >> file1.txt<<EOF
it has another line now
EOF
$ git add file1.txt
$ git diff --staged file1.txt
{% endhighlight %}

Where this *really* becomes handy is when you've only staged part of a file for commit.

{% highlight bash %}
$ sed "1 i\This line's now in front" -i file1.txt
$ echo "This line's now in back" >> file1.txt
$ git add -p file1.txt
# Select one change or the other.
$ git diff --staged
# There it is.
{% endhighlight %}

Enjoy :)
