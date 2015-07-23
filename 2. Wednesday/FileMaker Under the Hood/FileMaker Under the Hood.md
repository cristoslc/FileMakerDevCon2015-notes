# FileMaker Under the Hood


## If you look at FileMaker binaries, they change every time you open the file.

## FileMaker files are segmented into 4KB blocks

### so you don’t have to shift megabytes or terabytes when inserting into the “middle” of a file

### they contain the data of

#### layouts

#### scripts

#### table definitions

#### record contents

### blocks are linked together (forward & backward pointers)

### if you have a piece of data that is more than 4k, it gets split onto more than one block

### blocks fit where they fit.

### if you delete something, there’s an unused block in the middle of the file which can be reused (but might also sit there, empty but taking up disk space)

### blocks don’t have to be fully-filled

### Slide: Contents of a block as text

#### (slides unavailable for download)

## Every small piece of a file is addressed by an ID

### could be short, e.g. “10”

### or could be long, like “/10/01/01/1250120F143000000"

### IDs are sorted sequentially

#### when FM is looking for something, it does a quick search per-ID

#### IDs can be used to infer groups/types (e.g., /10 = custom functions)

## Q & A

### Is it safe to use a recovered file?

#### Yes, if no data was lost.

- Maybe can use FMDiff to tell?

#### If data gets lost (part of block cleared, or block dropped) then you don’t know what is missing.

### How does the consistency check work?

#### It looks at whether the record is present or not.

#### It doesn’t differentiate between structural or data records.

