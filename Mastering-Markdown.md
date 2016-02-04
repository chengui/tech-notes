# Mastering Markdown #

##  Overview ##

Markdown is a lightweight markup language with plain text formatting syntax designed. It was created by [John Gruber](https://en.wikipedia.org/wiki/John_Gruber) in 2004, with significant collaboration with [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz) on the syntax. The overriding design goal for Markdown's formatting syntax is to make it as readable as possible.

Meanwhile, Markdown is also a text-to-HTML conversion tool for web writers, written by Gruber in [Perl](), with the goal of allowing people "to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally  valid XHTML (or HTML). In this article, it always means the formatter, a plain text formatting syntax.

Sites such as [GitHub](), [reddit](), [Diaspora](), [Stack Exchange](),  [OpenStreetMap](), and [SourceForge]() use variants of Markdown to facilitate discussion between users. A Markdown dialect is also used by the instant message system [Slack]().

[^1]: https://en.wikipedia.org/wiki/Markdown

### Philosophy ###

The language is intended to be easy-to-read and easy-to-write as is feasible.
Readablity, however, is emphasized above all else. A Markdown formatted document should be publishable as-is, as plain text, and readable as-is, without looking like it's been marked up with tags or formatting instructions. To this end, its main inspiration is the existing conventions for marking up plain text in email, though it also draws from earlier markup languages[^1], notably [Setex](http://docutils.sourceforge.net/mirror/setext.html), [atx](http://www.aaronsw.com/2002/atx/), [Textile](http://textism.com/tools/textile/), [reStructuredText](http://docutils.sourceforge.net/rst.html), [Grutatext](http://www.triptico.com/software/grutatxt.html), and [EtText](http://ettext.taint.org/doc/).

### Inline HTML ###

Markdown's syntax is intended for one purpose: to be used as a format for *writing* for the web. It is compatible with HTML syntax in common, but comparing with HTML, Markdown is not a replacement, or even close to it. Its syntax is very small, coresponding only to a very small subset of HTML tags.

The pricinple is: HTML is a *publishing* format; Markdown is a *writing* format. Hence, you can simply use HTML itself in a Markdown document. But there are a little differences when processing block-level HTML tags and span-level HTML tags in a Markdown document.

Block-level HTML tags, e.g. `<div>`, `<table>`, `<pre>`, `<p>`, etc, must be separated from surrouding content by blank lines, and the start and end tags of the block should not be indented with tabs or spaces.

Span-level HTML tags, e.g. `<span>`, `<cite>`, or `<del>`, can be used anywhere in a Markdown paragraph, list item, or header. Unlike block-level HTML tags, Markdown syntax is processed within span-level tags.

### Extensions ###

As Gruber has argued that complete standardisation of Markdown whould be mistaken: "Different sites (and people) have different needs. No one syntax whould make all happy", there is no clearly defined Markdown standard, which led to fragmentation as different vendors write their own variants of Markdown to correct flaws or extend by adding missing features.

Among these Markdown extensions are [PHP Markdown Extra](), [MultiMarkdown](), [GitHub Flavoured Markdwn](), [Pandoc Markdown](). In some cases, this is to enable conversion into more formats than just HTML.

## Markdown Basic ###

This section offers an introduction of what it's like to use Markdown, and the language syntax described is completely based on [Daring Fireball]() statement by creator John Gruber.

### Headers ####

Markdown offers two styles of headers: *Setext* and *atx*. Setext-style headers are created by "underlining" with equal sign (=) and hyphens (-). And atx-style headers are formed by 1-6 hash marks (#) at the beginning of the line.

Setext-style headers:

    This is an H1
    ================
    This is an H2
    -------------

Atx-style headers:

    # This is an H1
    ## This is an H2

### Emphasis ####

In Markdown, asterisks (*) and underscores (_) are both used to indicate spans of emphasis. One * or _ will generate `<em>` tag, while double will generate `<strong>` tag.

    *italic*
    _italic_
    **bold**
    __bold__

### Blockquotes ####

Markdown uses email-style '>' angle brackets as indicators of blockquotes. And blockquotes can be nested by adding additional levels of >; also blockquotes can contain other Markdown elements, including headers, lists, and code blocks.

    > ## This is a header
    >
    > This is a blockquote.
    > > this is a nested blockquote.

### Lists ####

Markdown supports ordered (numbered) and unordered (bulleted) lists. Unordered (bulleted) list marks can be asterisks (*), pluses (+), and hypens (-); Ordered (numbered) lists use numbers followed by periods, while the numbers themselves are ignored.

Unordered lists:

    * Red
    * Green
    * Blud

Ordered lists:

    1. Bird
    2. McHale
    10. Parish

### Code ####

To write about programming or markup source code, you can create code spans or code blocks on demand. A code span is wrapped in backtick quotes, creating `<code>` tag respectively; And a code block is simply indented by at least 4 spaces or 1 tab at the start of the lines, generating both `<pre>` and `<code>` tags.

Inline code span:

    inline code wraps them in backticks: `var example = true`

Fenced code block:

    This is a normal paragraph:

        This is a code block.

### Links ####

Markdown supports two styles of links: *inline* and *reference*. In both styles, the link text is delimited by square brackets, the title attribute is optional, the link names are *not* case sensitive. The link URL may be surrounded by angle brackets optionally, and be refferring to a local resource by relative paths.

Inline-style link:

    This is [an example](http://example.com/ "Title") inline link.
    [This link](http://exmaple.net/) has no title attribute.

Reference-style link:

    This is [an example][id] reference-style link.

    [id]: http://example.com/ "Optional Title"

### Images ###

In Markdown, image syntax is very much like *Links* syntax, with looking like an exclamation mark (!) followed by link syntax. But instead of link name, the `alt` attribute text will be set for the image.
 
Inlink-style image:

    ![Alt text](/path/to/img.jpg)
    ![Alt text](/path/to/img.jpg "Optional Title")

Reference-style image:

    ![Alt text][id]

    [id]: url/to/image "Optional Title"

### Miscellaneous ###

TODO: 

## GitHub Flavoured Markdown ###

GitHub uses "GitHub Flavoured Markdown", or GFM. Comparing with Markdown Basic, it differs in a few significants ways and adds some additional functionality. GFM is used at most places around GitHub: [Gists](), comments in Issues and Pull Requests, and files with the `.md` and `.markdown` extension.

### Emphasis ###

Where standard Markdown transforms underscores (_) into italics, GFM ignores 
underscores in words.

GFM uses double tildes (~) to create strikethrough text, this is not availabe
in standard Markdown.

And GFM also supoorts URL autolinking, which allows you simply entering a URL
to be turned into a link directly.

    > do_this_and_do_that

    ~~strikethrough text~~

    http://example.com

### Fenced code blocks ###

Besides converting text with four spaces at the beginning of each line into a
code block like standard Markdown, GFM also supports wrapping your code in ` ``` ` to create fenced code blocks. But it's recommended to place a blank line before them.
  
    ```
    function test() {
        echo "notice the blank line before this function"
    }
    ```

### Syntax hightlighting ###

More further, GFM supports adding an optional language identifier in fenced code block to syntax hightlight the code. [Linguist] is used to perform language detection and syntax highlighting.

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("Hello World!")
    puts markdown.to_html
    ```
[linguist]: https://github.com/github/linguist

### Task Lists ###

GFM allows you to create a handy progress indicator like this:

    - [x] @mentions, #refs, [links](), **formatting**
    - [] this is an incomplete item

### Tables ###

GFM supports pipe-style tables, which allows you to create tables by separating each column with a pipe `|`, and the table header may be the first  row dividing other rows with hypens `-`.

And the colons within the header row indicate column alignment: a colon on the left-most side indicates a left-aligned column; a right-most one indicates a right-aligned column; a colon on both sides indicates a center-aligned column.

    fruit| price
    -----|-----:
    apple|2.05
    pear|1.37
    orange|3.09

### Emoji ###

GFM also suports emoji, to see the full list it supports, check out the [Emoji Cheat Sheet](http://www.emoji-cheat-sheet.com/).

    emoji!: :smile: :sparkles: :camel: :boom:

### Miscellaneous ###

TODO:

## PHP Markdown Extra ###

### Inside HTML ###

Markdown Extra allows you to put Markdown-formatted text content inside any block-level tag, by adding a *markdown* attribute to the tag which gives `markdown="1"`.

    <div markdown="1">
    This is *true* markdown text.
    </div>

### Special Attributes ###

    Header1  {#header1}
    =======

    ## Header2 ## {.main .shine #the-site lang=cn}

### Fenced Code Blocks ###

    ~~~~~~~~~~~~~~
    a code block
    ~~~~~~~~~~~~~~
    ````````````
    another code block
    ````````````

### Tables ###

    First Header | Second Header
    ------------ | -------------
    Content Cell | Content Cell
    Content Cell | Content Cell

### Definitions Lists ###

    Apple
    : Pomaceous fruit of plants
    : An American computer company

### Footnotes ###

    That's some text with a footnote.[^1]

    [^1]: And that's the footnote.

### Abbreviations ###

    *[HTML]: Hyper Text Markup Language
    *[W3C]: World Wide Web Consortium

    This HTML specification is maintained by the W3C.

### Miscellaneous ###

## MultiMarkdown ###

## Pandoc Markdown ###

## Markdown And Writing ##

### Markdown Editors ###

### Scientific Writing ###

### Pandoc ###

## Reference ##

> 1. Wikipedia: <https://en.wikipedia.org/wiki/Markdown>
> 2. Markdown Basic: <http://daringfireball.net/projects/markdown/>
> 3. Markdown Syntax: <http://daringfireball.net/projects/markdown/syntax>
> 4. GitHub Flavoured Markdown: <https://help.github.com/articles/github-flavored-markdown/>
> 5. GitHub Mastering Markdown: <https://guides.github.com/features/mastering-markdown/>
> 5. PHP Markdown Extra: <https://michelf.ca/projects/php-markdown/extra/>
> 6. Markdown Basic in Chinese: <http://wowubuntu.com/markdown/basic.html>
> 7. Markdown Syntax in Chinese: <http://wowubuntu.com/markdown/index.html>