Provides a faster algorithm to match regular expressions on character streams than the algorithm used by [streamflyer](http://code.google.com/p/streamflyer/).

## Usage ##

A typical example:
```
// choose the character stream to modify
Reader originalReader = ... // this reader is connected to the original data source

// we use FastRegexModifier instead of RegexModifier
Modifier fastModifier = new FastRegexModifier("edit(\\s+)stream", Pattern.DOTALL, "modify$1stream");

// create the modifying reader that wraps the original reader
Reader modifyingReader = new ModifyingReader(originalReader, fastModifier);

... // use the modifying reader instead of the original reader
```

In this example the chosen Modifier replaces the string "edit stream" with "modify stream". The modifier preserves the whitespace between "edit" and "stream".

## Why is this fast matcher not included in the [streamflyer project](http://code.google.com/p/streamflyer/) itself? ##

The code of the fast matcher relies on a modification of the
[java.util.regex](http://docs.oracle.com/javase/6/docs/api/java/util/regex/package-summary.html) package. The regex package is licensed with _GNU General Public License v2_ but the streamflyer project is licensed with _Apache License 2.0_. In order to deal with this license mismatch, the fast matcher is separated from the streamflyer project.

## Why licensed with GNU General Public License v2? ##

See above.

## Download ##

Go to the
[Installation page](http://code.google.com/p/streamflyer-regex-fast/wiki/Installation)
to get the latest release. This page provides also the Maven coordinates, prerequisites, and information about dependencies to other libraries.

## Questions, Suggestions, Issues ##

Please read the corresponding section on the web page of the [streamflyer project](http://code.google.com/p/streamflyer/#Questions,_Suggestions,_Issues).