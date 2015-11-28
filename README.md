# OpenOrienteering Mapper User Manual

This repository is the source of the OpenOrienteering Mapper User Manual.
It is online at http://openorienteering.github.io/mapper-manual/, and
it is merged into the released software packages.
User are encouraged to contribute to this manual on Github.

## Information for contributors

[Frontpage: index.md](/OpenOrienteering/mapper-manual/blob/gh-pages/pages/index.md)

The manual pages are in Markdown format, with some extensions.
HTML is supported, too.
The manual is published online by means of [Jekyll](http://jekyllrb.com/)
and offline in the release packages by means of
[Doxygen](http://www.stack.nl/~dimitri/doxygen/).
Only a subset of Markdown, Jekyll and Doxygen features is available for both
publishing paths.

### Guidelines

 - Pages must be named ending in ".md" (for Markdown).
 - Links to pages must use the .md ending, too.
 - There must be a cycle-free page/subpage hierarchy. This is use to for the
   contents tree in the offline documentation.
 - Don't edit files outside the pages directory.
 - Don't put to much effort in fancy formatting. (The HTML subset supported in
   the offline version is very limited.)
