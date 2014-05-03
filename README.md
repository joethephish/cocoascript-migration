CocoaScript Migration
=====================

Help &amp; documentation for your JSTalk → CocoaScript migration

As you probably know, Sketch will switch its scripting backend from JSTalk to CocoaScript in version 3.0.2.

As a result of this change, **some plugins will stop working unless you fix them**.

If you want to know whether your plugins are affected or not, run this on your plugins' root folder:

    grep -rwn -e YES -e NO -e copy -e '\[i\]' -e '\[1\]' -e intergerValue -e allSlices --include=*.{js,jstalk,sketchplugin} .

If you don't get any output, you're probably good to go (but then again, you should test your plugins just to make sure they work).

If you haven't done it already, [download the latest Sketch beta](http://bohemiancoding.com/sketch/beta/) and make sure your plugin(s) are working as expected.

We've created this repository to help you with this task. Here's a list of the issues we've identified, and how to solve them. We've tested 3.0.2 with some of the most popular plugins out there to find these, but we really need you to play with the beta and let us know if something is broken and is not on the list.

Feel free to file issues in this repo, and we'll either fix the bugs, or provide you with a workaround.

Thanks to all for your understanding, and for making Sketch awesome.


## Known Issues in Sketch 3.0.2 (7775)

### `copy` is now a reserved word

If you use it as a variable name in your scripts, they won’t work.

Found in:

- <https://github.com/makzan/Sketch-Plugin-Scripts>
- <https://github.com/tisho/sketch-plugins>

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
- <https://github.com/groove25/DrawingKit>
- <https://github.com/alessndro/sketch-plugins>

### `integerValue` is no longer working

If your script used `integerValue` to cast a number from a `[doc askForUserInput]` value, it will not work.

Use `parseInt(return_value)` instead if you need an integer (hint: most of the time you probably don't :)


## Other Issues

These issues are not exactly related to the CocoaScript migration, but are recent changes that you may want to check for while you're fixing other things.


### `allSlices` is deprecated

Use `exportableLayers` instead.

### `[MSArray length]` is deprecated

Use `[MSArray count]` instead.
