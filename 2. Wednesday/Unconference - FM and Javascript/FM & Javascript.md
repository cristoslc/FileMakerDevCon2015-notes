# FM & Javascript


## KEY TAKEAWAYS

### Data URI is no longer best practice. Instead, export files as a quasi-webapp to flat directories.

## Presenters

### Ryan Simms from Beezwax

#### will write a blog post next week (7 days from 2015-07-22 09:51 EST)

- will have modular file you can leverage

### Brian Schick from Beezwax

## Follow-up session

### Thursday at 2:00 PM - AJAX-type calls within a webviewer

## Using Data URI

### starting declaration with “data:text/html,”

### NOT a best practice anymore

#### You don’t want to intermix FileMaker data and web code (e.g., using merge fields).

- can’t take the code into other editors and have it run

- You want to be writing your code in a standard environment (not the calculation dialog).

- You want to be able to debug your code, using industry-best tools (e.g., Chrome, Firefox/Firebug, etc.).

## Current best practice

### Pushing tree structure from FileMaker to the temp directory.

#### can use Export Field Contents

#### (optional) can create folder structure, or could do it with flat structure

- hard to do in Go

#### when you export from Pro, it uses UTF-16

- when you export from Go, you get UTF-8 (which is better)

- to export UTF-8 text from FM on the desktop, uses an XSL file and then exports records using that XSL file

### Use namespacing

#### for the file type (js, css, html)

#### for YOUR solution

- because as the technique becomes more popular, you don’t want conflicts

- e.g., don’t use “index.html"

### Merging data from FileMaker

#### Method 1

- can then reference that object property in your app scripts

- generate JSON objects in FileMaker and export as .js files that add the data as a property to a core object

#### Method 2

- create a constructor function for the data array

#### Method 3

- can use HASH in URL (onHashChange listener) to send data from FileMaker

	- preserves state inside the HTML page because you don’t need to reload the webviewer

### Use file:// url to point at appropriate temp file from in your web viewer.

## WORKFLOW

### edit files directly from temp directory

#### lets you edit the files on disk, using your text editor

