---
layout: post
title: "How to remove a SSH host key"
date: 2013-04-29 19:45
comments: false
categories: [HOWTO, SSH]
---

There was a time before [Stack Overflow][1], when acquiring technical knowledge
on specific points through practical examples came very often from blog posts.
This may be a little less true since then, but it is still a good practice to
publicly share technical notes in case it could help someone or simply for
personal reference.

The previous and first post of this blog was the mandatory [hello world][2]. So
now that all the introduction is done, I will start with something usually
encountered when a new machine replace another one in a network. An appropriate
subject for the first real note.

<!-- more -->

The problem is trivial and occurs at the first SSH connexion if the new server
keeps the hostname of the old one:

    $ ssh alice@example.net
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
    Someone could be eavesdropping on you right now (man-in-the-middle attack)!
    It is also possible that a host key has just been changed.
    The fingerprint for the RSA key sent by the remote host is
    xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
    Please contact your system administrator.
    Add correct host key in /home/alice/.ssh/known_hosts to get rid of this message.
    Offending RSA key in /home/alice/.ssh/known_hosts:15
    RSA host key for example.net has changed and you have requested strict checking.
    Host key verification failed.

The manual available through `man ssh` contains a relevant entry:

> **ssh** automatically maintains and checks a database containing
> identification for all hosts it has ever been used with. Host keys are stored
> in `~/.ssh/known_hosts` in the user's home directory. Additionally, the file
> `/etc/ssh/ssh_known_hosts` is automatically checked for known hosts. Any new
> hosts are automatically added to the user's file. If a host's identification
> ever changes, **ssh** warns about this and disables password authentication
> to prevent server spoofing or man-in-the-middle attacks, which could
> otherwise be used to circumvent the encryption. The **StrictHostKeyChecking**
> option can be used to control logins to machines whose host key is not known
> or has changed.

Before going further, it is very important to understand the security
considerations of this warning as explained by the manual. It should not be
dismissed without being entirely sure of its cause.

Now in the case of a new server reusing the same hostname, it is perfectly
expected for the host key to have changed. And the solution is simply to edit
the file `~/.ssh/known_hosts` to remove the given line.

I used to do this modification by hand for years. At some point I switched to a
`sed` command for deleting the line without opening a text editor. But only
recently did I find out the existence of a very handy flag to `ssh-keygen` as
described by the manual:

> **-R** hostname
>
> Removes all keys belonging to _hostname_ from a _known_hosts_ file.
> This option is useful to delete hashed hosts (see the **-H** option
> above).

This command is worth remembering if the case occurs frequently:

    $ ssh-keygen -R "example.net"
    # Host example.net found: line 15 type RSA
    /home/alice/.ssh/known_hosts updated.
    Original contents retained as /home/alice/.ssh/known_hosts.old

The new host key will be automatically learned by `ssh` on the next connexion:

    $ ssh alice@example.net
    The authenticity of host 'example.net (xxx.xxx.xxx.xxx)' can't be established.
    RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
    Are you sure you want to continue connecting (yes/no)? yes
    Warning: Permanently added 'example.net' (RSA) to the list of known hosts.

[1]: http://stackoverflow.com
[2]: /blog/2013/04/15/hello-world
