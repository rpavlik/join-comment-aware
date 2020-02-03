# merge-line-smart

`join-comment-aware` will join lines and remove extraneous comment indicators,
as well as merging quoted string literals. if they continue across lines.
Previously when joining lines (e.g. via `ctrl+j` or `shift+j` in vim mode),
comment characters are kept and you'll have to remove them manually.

![demo](images/demo.gif)

Lines to join:

```sh
# This is a comment
# and this is the 2nd line
```

Old join style: 

```sh
# This is a comment # and this is the 2nd line
```

New join functionality:

```sh
# This is a comment and this is the 2nd line
```

Lines to join with string literals (new functionality added to predecessor
`join-comment-aware`):

```c++
"This is a string literal"
"and this is the 2nd line"
```

Old join style:

```c++
"This is a string literal" "and this is the 2nd line"
```

New join functionality:

```c++
"This is a string literal and this is the 2nd line"
```

## Build instructions

Make sure you have the deps:

```sh
npm install
```

Then build the `.vsix`:

```sh
npm run compile
npm run package
```

## Suggested Installation

This is available through the vscode standard installation (Not yet in the
vscode Marketplace).

I'd recommend replacing your normal join command (e.g. `ctrl+j` or `shift+j` in
vim mode) with `merge-lines-smart`. If a file type isn't recognized, it performs
the default behavior as before.

To replace the default join command *without* vim mode (`ctrl+j`), add this to
your `keybindings.json`:

```json
{
  "key": "ctrl+j",
  "command": "mergeLineSmart.merge",
  "when": "terminalFocus"
}
```

To replace the default join command *with* vim mode (`shift+j`), add this to
your `settings.json`:

```json
{
  "vim.otherModesKeyBindingsNonRecursive": [
    {
      "before": ["J"],
      "after": [],
      "commands": [
        {
          "command": "mergeLineSmart.merge",
          "args": []
        }
      ]
    }
  ]
}
```

## Known Issues

The following file types are supported with comment-awareness joining.
Otherwise, default join behavior will take over.

- ruby
- python
- javascript
- java
- json
- csharp
- cpp
- go
- php

## Release Notes

Initial `merge-lines-smart` release. Builds on
[`join-comment-aware` 0.0.3](https://github.com/johngraham262/join-comment-aware):
thank you to @johngraham262 for a great starting place.

### 0.0.4

First version of `merge-lines-smart`.

### 0.0.3

Tweak README example.

### 0.0.2

Add icons. Update version so VS Marketplace can udpate.

### 0.0.1

Initial release of `join-comment-aware`
