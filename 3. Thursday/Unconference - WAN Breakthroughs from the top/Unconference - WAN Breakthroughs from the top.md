# Unconference - WAN Breakthroughs from the top


## Presenter

### Scott

#### runs Apple customer care call centers

#### built a database that’s used globally to do high level analysis of customer calls

#### data is worth over $40 million

## How I got here…

### Summary fields for counts were slow

#### created data-side self-join

## 3 ways to speed up reporting over wan

### proxy tables

#### de-normalized “placeholder” tables

- candidates for denormalization

	- calculations

	- summaries

	- fields to be sorted on

	- deeply-nested data

#### Attributes of proxy tables

- “Flattened” table data

- synchronized by auto-enter calc and scripting

	- server-side script every 2 minutes

		- if there isn’t a proxy record for the cases attached to an issue, create the proxy records

		- if there are issues without cases attached, remove them from the proxy table

### list view instead of sub-summary report

#### Pros

- faster scrolling, sorting, refreshing than sub-summary reports

- easier to code & test

- Summary reports that contain more than 560 records run into “Unexpected behaviors”

	- can’t get past 560th record

#### Cons

- difficult to create dynamic, hierarchical reports

	- List in UI file might solve?

- Data not updated in real-time

- Larger data file size due to redundancy of data and increased indexing (de-normalization)

- requires additional tables & fields (redundancy, contributing to data bloat)

- requires scripts for refresh (affects timeliness)

### scripting

## Dumb data (number/text values) vs evaluated fields (unstored/normalized)

### Evaluations over WAN

#### FM caches only 25 records at a time

#### index fields sort much faster

#### avoid unstored calcs

#### avoid summary fields

#### avoid deeply-nested relationships

## Camp Software/BE Plugin

### uses SQL to update related records when parent record is changed

#### needs GLOBAL fields for data entry

#### uses an auto-enter calculation in the PARENT record

- which runs an SQL statement, which performs an update on the CHILD records

#### sends data as parameters to PSoS

#### can be run in parallel (optionally)

#### add boolean logic and scheduled server script to ensure sync

## Misc

### created a database, with a record for each scheduled script

#### allowed a visual matrix to determine how to do load balancing

- [CLC:] this could also be solved with the PSOS management queue concept

### Apple has an app that will help you simulate a slow connection on your computer

#### http://nshipster.com/network-link-conditioner/

## Q & A

### Do you have to send the actual value, not a reference to the value, when Performing Script on Server?

#### yes...ish?

### Are you then doing sub-summaries of the proxy data?

#### yes

#### still stay away from unstored calcs

#### performs better than on original table, but will be somewhat slower than a List view

### Known bug

#### If you are running a script in a file that has some dependency on a file hosted on another FileMaker server, the server-side script / PSoS will give a “file missing” error.

- due to an issue in passthrough authentication

