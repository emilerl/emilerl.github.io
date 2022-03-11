---
title: "Minor Eclipse Util Plugin"
date: 2006-02-28T19:07:00+01:00
draft: false
---

I have discovered that during development in Eclipse, you sometimes have to restart the workbench for various reasons. The “File->Switch workspace” feature is ok for that I guess, but sometimes when you are working with several different workspaces, the value in the switch workspace dialog is not in sync with what you are currently using – which will cause some unecessary delay.

Since it is so little effort needed creating something that just restarts from the current workspace, I decided to create a plug-in for it and publish it for anyone who feel the need to be able to restart Eclipse swiftly.

The only piece of code needed (except the bulk of plugin.xml, manifest etc..) is these lines in the action:
```java
public void run(IAction action) {
	PlatformUI.getWorkbench().restart();
}
```

