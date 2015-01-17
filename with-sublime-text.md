Recommend text editor is sublime text 3.

### Let's go with it.

Install the sublime text 3.

Install the package control.

At last, install [editor config supprot pluggin](https://github.com/sindresorhus/editorconfig-sublime).

### Recommend config

```
# editorconfig.org
root = true

# Unix-style newlines with a newline ending every file
[*]
end_of_line = lf
insert_final_newline = true
charset = utf-8

[*.php]
indent_style = space
indent_size = 4
trim_trailing_whitespace = true

[*.{js,twig,css,scss,html}]
indent_style = space
indent_size = 2

[{Gruntfile.js,bower.json,composer.json,package.json}]
indent_style = space
indent_size = 2

[*.md]
trim_trailing_whitespace = false

```

### More

see what is [editorconfig](http://editorconfig.org/)
