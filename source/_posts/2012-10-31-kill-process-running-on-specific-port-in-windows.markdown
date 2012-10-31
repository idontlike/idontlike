---
layout: post
title: kill "8080 process"
date: 2012-10-31 21:11
comments: true
categories: [windows, win terminal]
---
 1. open *cmd.exe* as admin (start->search cmd...right click)
 2. netstat -a -n -o |findstr :8080
 3. TaskKill.exe /f /PID ###


