---
layout: post
title: "Count IP Addresses in Access Log "
date: 2014-01-06 09:31:05 +0700
comments: true
author: Kao Nhan
categories: English log shell
---

**$**echo "most frequent IPs in last 10000 lines in log"

```
sudo tail -10000 /var/log/nginx/lazyadmin.me.log | awk ‘{print $1}’ | sort | uniq -c | sort -g

```

