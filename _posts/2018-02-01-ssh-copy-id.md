---
layout: post
title: "TIL: Using ssh-copy-id to install public keys on hosts"
category: til
tags: [ssh]
---
For years I have been manually adding my SSH public keys to the `~/.ssh/authorized_keys` file (like an animal) on systems that I SSH into. 
It turns out that there's an automated way to do this - `ssh-copy-id`. 

In the simplest case, just running:
```
ssh-copy-id <host>
```
will install either the newest public key in your `~/.ssh/` directory or (if you are using the `ssh-agent`) it will install all of the keys returned by `ssh-add -L`. 

So, if you want to be picky about which key(s) get installed you can either `touch` the public key file you want to use, or only have in `ssh-agent` the key(s) you want to install - e.g.:
```
# Delete any existing keys in the ssh-agent
ssh-add -D

# Add the key we want to use to the ssh-agent
ssh-add ~/.ssh/id_ed25519

# Copy the public keys to the remote host
ssh-copy-id <host>
```

(A pleasant side effect of using this is that I should never need to type the American spelling of "authorised" again)