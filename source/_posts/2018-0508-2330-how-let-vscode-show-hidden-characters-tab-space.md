---
title: how let vscode show hidden characters (tab,space...)
date: 2018-05-08 23:30:00
updated: 2018-05-08 23:30:00
tags: [vscode]
---

* i like set editer default show the hidden characters to a symbol,
  because that can avoid when i copy a static demo into my code,
  and that have a lot tab.

{% asset_img 1.png "tabs in code" %}

<!--more-->

* go to vscode preferences use "cmd + ," hotkey.

* add this setting to option 

```
"editor.renderWhitespace": "all",
```

reference : 
[github vscode issue](https://github.com/Microsoft/vscode/issues/18282)
