# Unconference - Web Viewer Applications


## KEY TAKEAWAYS

### onHashChange is used to send small(er) amounts of information TO the webviewer

### JSON-P is used to send large(r) amounts of information TO the webviewer

### Limited to 2000 characters in URL in Windows

## Presenters

### Ryan Simms from Beezwax

### Christopher Vine from Threeprong

## Follow-up

### go to Beezwax blog

#### look for posts about FMAjax

## onHashChange - used to send limited information to the webviewer

### “AJAX-ish”

### if you go into your browser bar and just hit return, it reloads (i.e., if hash is unchanged).

#### but if you add anything new to the hash, then it doesn’t reload

#### the hash is NOT sent to the server — there is no network activity associated with it

### prevents losing state

### more modern feel for application

### if moving lots of information, may be better to export it (e.g., as JSON) to a file, then use hash to tell the script to reload the data

## how to send large info to the webviewer?

### 2000 character limit on URLs in Internet Explorer, so can’t do it in hash (cross-platform)

### CORS can make it tricky to do using local files

#### == Cross Origin Resource Sharing

#### Different browsers treat local files differently from CORS URL requests

- internet explorer and current Safari have CORS issue when trying to “ajax-ly” load from a local file (file://) - only works for http://

- still works in web viewers on Mac, but probably not for too much longer

### JSONP - the safe way to do it using local files

#### http://json-p.org/

#### JSON with padding

#### you get data that’s wrapped in a callback function

- calling the function gives you the data

#### <script> tag

- can be loaded dynamically

	- use javascript to insert the script tag to the DOM

- will go get the referenced script and executes it

## how to send information from web viewer back to FileMaker?

### small amounts

#### fmp:// URL

### book-sized amounts

#### on Windows

- can use clipboard

	- https://www.lucidchart.com/techblog/2014/12/02/definitive-guide-copying-pasting-javascript/

- can split the string and call an fmp:// URL many times

#### on Mac, can encode it in the URL

#### can use CWP and POST from HTML page to FileMaker

## Gotchas

### if a web viewer calls an fmp url while script is busy, call is ignored

#### web viewer also stops updating while script is busy

- put in a script pause of 0.1 seconds (or maybe even less?)

#### time may not pass correctly in a web viewer — its processing is paused while FMP is busy with a script

### local storage and web sql not available

### time in the web viewer may not be the same as time in FMP

### when namespacing, may want to include server name (to avoid namespace conflicts for same file open on two different servers)

#### maybe also pre-/ap-pend a timestamp, for the same file opened multiple times locally?

## Q & A

### what about writing temp files containing sensitive data?

#### if small bits of data, send directly

#### temp directory doesn’t get cleared if FileMaker crashes

### does 2000 character limit apply to things in the FileMaker calculation dialog?

#### Yes, but not sure if it will just fail or if it will truncate.

