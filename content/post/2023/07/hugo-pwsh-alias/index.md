---
date: '2023-07-12T00:00:00+00:00'
description: ''
slug: 2023/07/hugo-pwsh-alias
title: 'Use an alias in your PowerShell profile to create a new Hugo post'
image: 'windows-powershell-eyecatch-4060478705.png'
categories:
 - 
tags:
 - pwsh
---

The command to create a new Hugo post is:

```pwsh
hugo new <path to new content>
```

### Use an alias

Using Powershell, you can use an alias to make this easier, here is the block of code we are going to use:

```pwsh
function New-HugoPost {
  param (
    [string]$PostName
  )
 
  # UPDATE ME TO POINT TO YOUR BLOG PATH
  $blogPath = "c:\path\to\your\blog"

  set-location $blogPath
  & hugo.exe new "content\post\$PostName\index.md" -c $blogPath
}

Set-Alias nhp New-HugoPost
```

This can be reloaded each time Powershell starts by editing your profile:

```pwsh
# open up the profile
notepad $profile
#
# ** paste in the code block above & save **
# 
# reload the profile
. $profile
```

### Test it works

Then, to create a new post using the new, friendly ``nhp`` alias:

```pwsh
nhp my-new-post
```
