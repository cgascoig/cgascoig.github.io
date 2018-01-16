---
layout: post
title: "TIL: Use SSH ProxyJump"
category: til
tags: [ssh]
---
An easy (and much nicer than using ProxyCommand and/or ForwardAgent) way to "proxy" or "jump" through a bastion host to a private host. In `~/.ssh/config`:
```
Host private_host
  ProxyJump bastion_host
```

Or on the command line:
```
ssh -J bastion_host private_host
```