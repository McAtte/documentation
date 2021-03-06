---
layout: default
title: readfile
categories: [Reference, Functions, readfile]
published: true
alias: reference-functions-readfile.html
tags: [reference, io functions, functions, readfile]
---

[%CFEngine_function_prototype(filename, maxbytes)%]

**Description:** Returns the first `maxbytes` bytes from file
`filename`.  When `maxbytes` is 0, the maximum possible bytes will be
read from the file (but see **Notes** below).

[%CFEngine_function_attributes(filename, maxbytes)%]

**Example:**

Prepare:

[%CFEngine_include_snippet(readfile.cf, #\+begin_src prep, .*end_src)%]

Run:

[%CFEngine_include_snippet(readfile.cf, #\+begin_src cfengine3, .*end_src)%]

Output:

[%CFEngine_include_snippet(readfile.cf, #\+begin_src\s+example_output\s*, .*end_src)%]

**Notes:**

* To reliably read files located within /proc or /sys directories,
`maxsize` has to be set to `0`.

* At the moment, only 4095 bytes can fit into a string variable.  This
limitation may be removed in the future.  If this should happen, a
warning will be printed.

* If you request more bytes than CFEngine can read into a string
variable (e.g. `999999999`), a warning will also be printed.

* If either because you specified a large value, or you specified `0`,
more bytes are read than will fit in a string, the string is
truncated to the maximum.

**History:** Warnings about the size limit and the special `0` value were introduced in 3.6.0
