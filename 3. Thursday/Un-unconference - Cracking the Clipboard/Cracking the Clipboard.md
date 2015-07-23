# Cracking the Clipboard


## Presenter

### Daniel from New York Hotel & Motel Trades Council

#### dshockley@nyhtc.org

## starter code is on github

### https://github.com/DanShockley/FmClipTools

### everything is applescripts

### they use Keyboard Maestro to trigger scripts, but could easily use Alfred Workflows or your applescript launcher of choice

## what’s in the clipboard

### XML, looks a lot like the DDR

### can’t be pasted directly in to a text editor, because the datatype is not text

### clipboards can contain more than one object type, but (by default) only one of each object type

## Can do it within your file, or within a runtime

### BaseElements plugin

#### has ability to get and set clipboard object types

### advantage of runtime is that it creates a separate application, so you can keep it open in parallel to your work in FileMaker

## Not clipboard-related

### “Developer” privilege set instead of “[Full Access]”

#### use scripts that have “Run as Full Access” to do things like open Manage Database

#### could apply to Implementors

