---
layout: post
title: Converting .doc, .pdf, and .html
---

In 2014, I was trying to make a webapp that could save documents as `.pdf` and `.doc` files. These are a series of notes, only loosely edited, of the findings I had along the way:

# Option 1: Use unoconv

1. Install `Libreoffice 4.3.x` on the server
2. Install `unoconv` from master on the server
3. Use `bash` to convert documents (see unoconv docs)

## Gotchas:

There's a special page style for HTML documents. You have to change that page style in order to have the changes reflected when converting from HTML to other document types.

### Create Libreoffice Templates! (.ott) files

* Open up the `Styles and Formatting` pane (wrench icon on top left, of F11)
* Go to the `Page Styles` tab
* Change the HTML style to reflect what the page should look like with HTML
* Save as a template (.ott) file

# Option 2: Use soffice

1. Install `Libreoffice 4.3.x` on the server (where the app is running)
2. Point to `libreoffice-install/program/soffice` (either exe for Windows, or the executable soffice for unix) via the PATH or your `.bashrc` file
3. Use `bash` to convert documents

---

## Bash commands:

    soffice --headless --convert-to [document type] --output-dir [output directory] [file to convert]
    
* `document type` the file format to convert to. `pdf`, `doc`, `docx`, `html`, etc. are all fair game.
* `output directory` the directory to output to. If left blank, will output to the current working directory.
* `file to convert` the file to convert. TODO: figure out how to convert from a stdin buffer
    
As an example:

    soffice --headless --convert-to docx --output-dir /doc index.html