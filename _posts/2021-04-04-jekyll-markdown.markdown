---
layout:     post
title:      "Markdown Cheatsheet"
subtitle:   "Jekyll Markdown Reference"
date:       2021-04-04 13:00:00
author:     "Sofia"
header-img: "img/post-default-bg.jpeg"
catalog: true
tags:
    - Jekyll
    - Markdown
---

# Table of Contents  
[Headers](#headers)  
[Emphasis](#emphasis)  
[Lists](#lists)  
[Links](#links)  
[Images](#images)  
[Tables](#tables)  
[Blockquotes](#blockquotes)  
[Inline HTML](#html)  
[Horizontal Rule](#hr)  
[Line Breaks](#lines)  
[YouTube Videos](#videos)  

<a name="headers"/>

# Headers
```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```
... becomes ...

> # Heading 1
> ## Heading 2
> ### Heading 3
> #### Heading 4
> ##### Heading 5
> ###### Heading 6

<a name="emphasis"/>

# Emphasis

```markdown
Emphasis, aka italics, with *asterisks* or _underscores_.
Strong emphasis, aka bold, with **asterisks** or __underscores__.
Combined emphasis with **asterisks and _underscores_**.
Strikethrough uses two tildes. ~~Scratch this.~~
```

... becomes ...


> Emphasis, aka italics, with *asterisks* or _underscores_.
> Strong emphasis, aka bold, with **asterisks** or __underscores__.
> Combined emphasis with **asterisks and _underscores_**.
> Strikethrough uses two tildes. ~~Scratch this.~~


<a name="lists"/>

# Lists

(In this example, leading and trailing spaces are shown with with dots: ⋅)

```markdown
1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
```
... becomes ...

> 1. First ordered list item
> 2. Another item
>   * Unordered sub-list.
> 1. Actual numbers don't matter, just that it's a number
>   1. Ordered sub-list
> 4. And another item.
>    You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).  
>    To have a line break without a paragraph, you will need to use two trailing spaces.  
>    Note that this line is separate, but within the same paragraph.    
>    (This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)
> * Unordered list can use asterisks
> - Or minuses
> + Or pluses

<a name="links"/>

# Links

There are two ways to create links.

```markdown
[I'm an inline-style link](https://www.google.com)
[I'm an inline-style link with title](https://www.google.com "Google's Homepage")
[I'm a relative reference to a repository file](../blob/master/LICENSE)
[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

[1]: http://slashdot.org
[link text itself]: http://www.reddit.com
```
... becomes ...

> [I'm an inline-style link](https://www.google.com)  
> [I'm an inline-style link with title](https://www.google.com "Google's Homepage")  
> [I'm a relative reference to a repository file](../blob/master/LICENSE)  
> [You can use numbers for reference-style link definitions][1]

> Or leave it empty and use the [link text itself].

> [1]: http://slashdot.org
> [link text itself]: http://www.reddit.com

<a name="images"/>

# Images

```markdown
Inline-style:
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style:
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"
```
... becomes ...

> Here's our logo (hover to see the title text):  
> Inline-style:  
> ![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")  
> Reference-style:  
> ![alt text][logo]  
>
> [logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

<a name="tables"/>

# Tables

Tables aren't part of the core Markdown spec, but they are part of GFM and *Markdown Here* supports them. They are an easy way of adding tables to your email -- a task that would otherwise require copy-pasting from another application.

```markdown
Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the
raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3
```
... becomes ...

> Colons can be used to align columns.
>
> | Tables        | Are           | Cool |
> | ------------- |:-------------:| -----:|
> | col 3 is      | right-aligned | $1600 |
> | col 2 is      | centered      |   $12 |
> | zebra stripes | are neat      |    $1 |
>  
> There must be at least 3 dashes separating each header cell. The outer pipes ( \| ) are optional, and you don't need to make the raw Markdown line up prettily. You can also use inline Markdown.
>
> Markdown | Less | Pretty
> --- | --- | ---
> *Still* | `renders` | **nicely**
> 1 | 2 | 3

<a name="blockquotes"/>

# Blockquotes

```m
> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.
```

becomes:

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.

<a name="html"/>

# Inline HTML

You can also use raw HTML in your Markdown, and it'll mostly work pretty well.

```no-highlight
<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>
```

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>

<a name="hr"/>

# Horizontal Rule

```
Three or more...

---

Hyphens

***

Asterisks

___

Underscores
```

Three or more...

---

Hyphens

***

Asterisks

___

Underscores

<a name="lines"/>

# Line Breaks

My basic recommendation for learning how line breaks work is to experiment and discover -- hit &lt;Enter&gt; once (i.e., insert one newline), then hit it twice (i.e., insert two newlines), see what happens. You'll soon learn to get what you want. "Markdown Toggle" is your friend.

Here are some things to try out:

```
Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.
```

Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also begins a separate paragraph, but...  
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.

(Technical note: *Markdown Here* uses GFM line breaks, so there's no need to use MD's two-space line breaks.)

<a name="videos"/>

# YouTube Videos

They can't be added directly but you can add an image with a link to the video like this:

```no-highlight
<a href="http://www.youtube.com/watch?feature=player_embedded&v=YOUTUBE_VIDEO_ID_HERE
" target="_blank"><img src="http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg"
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>
```

Or, in pure Markdown, but losing the image sizing and border:

```no-highlight
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](http://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)
```

Referencing a bug by #bugID in your git commit links it to the slip. For example #1.

---

License: [CC-BY](https://creativecommons.org/licenses/by/3.0/)

Credit: [nycdh-jekyll](https://github.com/mnyrop/nycdh-jekyll/blob/master/docs/markdown-cheatsheet.md)