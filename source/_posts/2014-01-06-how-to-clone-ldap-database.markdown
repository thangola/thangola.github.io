---
layout: post
title: "How to clone LDAP Database"
date: 2014-01-06 09:45:45 +0700
comments: true
categories: ldap
---

With root, run command to Export your DB with slapcat:

``` 
slapcat > ldif 
```

Import the DB with slapadd (make sure the LDAP server is stopped):

```
slapadd -l ldif
```
