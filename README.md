cocoascript-migration
=====================

Help &amp; documentation for your JSTalk → CocoaScript migration

## Notes for Plugin Developers

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
