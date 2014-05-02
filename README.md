CocoaScript Migration
=====================

Help &amp; documentation for your JSTalk → CocoaScript migration

As you probably know, Sketch will switch its scripting backend from JSTalk to CocoaScript in version 3.0.2.

As a result of this change, **some plugins will stop working unless you fix them**.

We've created this repository to help you with this task. Here's a list of the issues we've identified, and how to solve them. We've tested 3.0.2 with some of the most popular plugins out there to find these, but we really need you to play with the beta and let us know if something is broken and is not on the list.

Feel free to file issues in this repo, and we'll either fix the bugs, or provide you with a workaround.

Thanks to all for your understanding, and for making Sketch awesome.


## Known Issues in Sketch 3.0.2 (7775)

### `copy` is now a reserved word

If you use it as a variable name in your scripts, they won’t work.

Found in:

- <https://github.com/makzan/Sketch-Plugin-Scripts>

### `YES` and `NO` have been removed

In JSTalk, `YES` and `NO` were aliases to `true` and `false`. This is no longer the case in CocoaScript, so you should replace them with proper boolean values.

Alternatively, you can add this preamble to your scripts:

    var YES = true
    var NO = false

This issue has been found in:

- <https://github.com/timuric/Content-generator-for-sketch-app>

### JavaScript-like syntax to access elements in MSArrays doesn’t work

Example:

    [group layers][1]

worked in 3.0, but now you’d need to do:

    [[group layers] objectAtIndex:1]

or:

    [group layers].array()[1]

This issue has been found in:

- <https://github.com/timuric/Content-generator-for-sketch-app>
