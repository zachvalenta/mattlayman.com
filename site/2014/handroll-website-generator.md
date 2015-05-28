%YAML 1.1
---
title: "handroll: a simple website generator"
template: writing.j2
date: May 4, 2014
---
Simplicity. That was my goal after studying [DHH's personal
website](http://david.heinemeierhansson.com/). I wanted a simple website that
had all the feeling of something handcrafted, but I didn't want to write all
my HTML by hand. I looked at the website generators out there like
[Pelican](http://blog.getpelican.com/) (which is pretty great if you want
blogging software), but they didn't fit my use case. I wanted complete control.
Is that too much to ask? No. So I scratched my own itch and wrote some new
software. I called it **handroll**. Let me show an example:

```bash
$ handroll site mblayman.github.io
```

My source content is in the `site` directory. The output will be stored in my
`mblayman.github.io` git repository so I can easily publish my work to
[http://mblayman.github.io](http://mblayman.github.io). handroll copies all the
content of `site` to `mblayman.github.io`. When it finds a Markdown file
(`*.md`), it generates HTML and combines it with `template.html` from the root
of the site directory. The first line of the Markdown file is passed to the
template as `title` and the generated HTML of the remainder of the file is
passed as `content`. If the template was:

```html
<!DOCTYPE html>
<html>
<head>
  <title>${title}</title>
</head>
<body>
  <h1>${title}</h1>
  ${content}
</body>
</html>
```

And `index.md` was:

```
A Sample Site Title

## Another heading

This is text in the body
```

Then the resulting `index.html` would be:

```html
<!DOCTYPE html>
<html>
<head>
  <title>A Sample Site Title</title>
</head>
<body>
  <h1>A Sample Site Title</h1>
  <h2>Another heading</h2>
<p>This is text in the body.</p>
</body>
</html>
<!-- handrolled for excellence -->
```

You can get handroll by installing it the standard Python way:

```bash
$ pip install handroll
```

I am doing development of handroll on
[GitHub](https://github.com/mblayman/handroll).