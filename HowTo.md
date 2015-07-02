# Getting started with the terminal library #

```
import terminal
```

## Examples: ##
### Adding color to text ###

```
"""Wrap text in ANSI/SGR escape codes."""
print '%s %s' % (terminal.AnsiText('Hello', ['red']),
                 terminal.AnsiText('World', ['yellow', 'bold'])
```

**=>** <font color='red'>Hello</font><b><font color='orange'> World</font></b>

### Stripping color from text ###
```
"""Strip ANSI/SGR escape sequences from text."""
txtstring = '%s %s' % (terminal.AnsiText('Hello', ['red']),
                       terminal.AnsiText(' World', ['yellow', 'bold'])
print StripAnsiText(txtstring)
```

**=>** Hello World

### Determining Terminal dimensions ###

```
"""Returns terminal length and width as a tuple."""
terminal.TerminalSize()
```

**=>** (24, 80)

### Formatting Text to Display Dimensions ###

```
"""Break line to fit screen width, factoring in ANSI/SGR escape sequences."""
txtstring = 'A string displayed on a terminal 20 characters wide.'
print terminal.LineWrap(txtstring)
```

**=>**
<br>"A string displayed<br>
on a terminal 20<br>
characters wide."<br>
<br>
<h3>Interactively Paging Through Text</h3>

<pre><code>"""Supports paging of text on a terminal, somewhat like a simple 'more' or 'less'."""<br>
largetextblock = """Once upon a time ..."""<br>
pager = terminal.Pager()<br>
pager.Page(text=largetextblock)<br>
</code></pre>