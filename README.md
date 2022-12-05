# Payloads to...

* [Fetch an external resource](fetch.md)

# Introduction

The payloads described in the various files may need wrapping to put them in a JavaSscript context (unless the injection ends up already inside a JS context, which is rare). Possible ways to execute a payload are:

* If injection ends up outside of an HTML tag:
  * `<script>`**_payload_**`</script>`
  * `<svg/onload="`**_payload_**`"/>`
  * `<img/onerror="`**_payload_**`"/src=x>`
  * `<style/onload="`**_payload_**`"></style>`
  * `<input/onfocus="`**_payload_**`"/autofocus>`
  * `<marquee/onstart="`**_payload_**`"></marquee>`
  * `<div/onwheel="`**_payload_**`"/style="height:200%;width:100%"></div>`
  * `<div/onmouseover="`**_payload_**`"/style="height:100%;width:100%"></div>`
  * ... many more, see below table for event attributes and supported tags
* If injection ends up inside an HTML tag's attribute:
  * `" `**_event_**`="`**_payload_**
  * `' `**_event_**`='`**_payload_** *(replace single quotes in payload with double quotes)*

##### Event handlers
Possible events and the supported HTML tags are:

| event         | supported HTML tags |
|---------------|---------------------|
| onload        | body, frame, frameset, iframe, img, input type="image", link, script, style |
| onchange      | input type="checkbox", input type="file", input type="password", input type="radio", input type="range", input type="search", input type="text", select, textarea |
| onkeyup       | **all except** base, bdo, br, head, html, iframe, meta, param, script, style, title |
| onmouseover   | &#x2014;"&#x2014; |
| onblur        | &#x2014;"&#x2014; |
| onfocus       | &#x2014;"&#x2014; |
| onclick       | &#x2014;"&#x2014; |
| onmouseover   | &#x2014;"&#x2014; |
| onmouseout    | &#x2014;"&#x2014; |
| oncontextmenu | **all, but it can only be triggered if the element takes space on the page** |
| onwheel       | &#x2014;"&#x2014; |
| ondrag        | &#x2014;"&#x2014; |
| ondrop        | &#x2014;"&#x2014; |
| oncopy        | &#x2014;"&#x2014; |
| oncut         | &#x2014;"&#x2014; |
| onpaste       | &#x2014;"&#x2014; |
| onscroll      | address, blockquote, body, caption, center, dd, dir, div, dl, dt, fieldset, form, h1&#x2014;h6, html, li, menu, object, ol, p, pre, select, tbody, textarea, tfoot, thead, ul |
| oninvalid     | input |
| oninput       | input type="password", input type="search", input type="text", textarea |
| onsearch      | input type="search" |
| onselect      | input type="file", input type="password", input type="text", textarea |
| onreset       | form |
| onsubmit      | form |

##### NOTES
* Some WAFs block only some html tags (e.g. `<script>`), but not other tags, so don't give up after trying a few that got rejected.
* Some WAFs do a poor job and fail to block HTML tags or attributes when they are capitalized (or mixed case). Give that a try.
* Many event handlers require user action. See more at `https://www.w3schools.com/TAGS/ev_`**_event_**`.asp`



#### Script Explained:

This code is a Python script for encoding payloads to be used in cross-site scripting (XSS) attacks. A payload in this context is a piece of JavaScript code that is sent to a web server in order to exploit a vulnerability in the server-side code.

The script has a number of functions and classes that are used to format, split, and encode the payload so that it can be delivered to the server in a way that avoids detection.

The script begins by importing a number of modules that it will use, including `sys, argparse, string, logging, and re`. These modules provide various functions that are used for input/output, command-line argument parsing, string manipulation, logging, and regular expressions.

Next, the script defines a number of colors that can be used for logging messages. This is used to make the log output more readable by coloring different types of messages differently.

The `ColorFormatter class` is then defined, which is a subclass of the `logging.Formatter class`. This class is used to format log messages in a way that includes color codes to display the messages in the appropriate colors.

The `MAX_JS_INT` constant is defined next, and is set to the maximum safe integer value in JavaScript.

The Payload class is then defined, which is used to represent a payload as a string. This class provides methods for appending, prepending, and splitting the payload string into multiple lines.

The `split_to_len` function is defined next, which takes a string and a maximum length and splits the string into multiple lines, each of which has at most the specified maximum length. This is used to split the payload into multiple lines that can be encoded and delivered to the server in a way that avoids detection.

The `main` function is then defined, which is the entry point for the script. This function parses the command-line arguments, sets up logging, and then processes the payload based on the specified options.

Overall, this script provides a means for encoding payloads for use in XSS attacks in a way that avoids detection.
