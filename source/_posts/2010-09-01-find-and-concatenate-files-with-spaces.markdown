---
date: '2010-09-01 11:19:45'
layout: post
slug: find-and-concatenate-files-with-spaces
status: publish
title: Find and Concatenate Files with Spaces
wordpress_id: '1048215519'
categories:
- regular
---

Normally, xargs will interpret the spaces in the filenames as separate files. The `-print0` argument to find paired with the `-0` argument to xargs will use some other magical delimiter so that the spacey filenames remain intact as you pipe them around.





`  

find ./spacey_files -name *Report* -type f -print0 | xargs -0 cat > all_reports.csv  
`
