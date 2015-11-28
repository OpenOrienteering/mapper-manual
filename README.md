# OpenOrienteering Mapper User Manual

This repository is the source of the OpenOrienteering Mapper User Manual.
It is online at http://openorienteering.github.io/mapper-manual/, and
it is merged into the released software packages.
User are encouraged to contribute to this manual on Github.

## Information for contributors

[Frontpage: pages/index.md](https://github.com/OpenOrienteering/mapper-manual/blob/gh-pages/pages/index.md)

Pages may be edited directly on Github which even features a preview.

The manual pages are written in Markdown format, with some extensions.
HTML is supported, too.
The manual is published online by means of [Jekyll](http://jekyllrb.com/)
and offline in the release packages by means of
[Doxygen](http://www.stack.nl/~dimitri/doxygen/).
Only a subset of Markdown, Jekyll and Doxygen features is available for both
publishing paths.

### Guidelines

 - Don't put or modify files outside the pages directory unless you know what you are doing.
   (Only this directory is merged back to the mapper repository.)
 - Pages must be named ending in ".md" (for Markdown).
 - Links to pages must use the .md ending, too.
 - There must be a cycle-free page/subpage hierarchy.
   (This is used for the contents tree in the offline documentation.)
   To create a page/subpage relation, put ```{: .subpage}``` behind the link to the "subpage" in the "page" (cf. [frontpage](pages/index.md)).
 - Don't put to much effort in fancy formatting.
   (The HTML subset supported in the offline version is very limited.)
 - Put images in the pages/images directory if they are used only in the documentation (e.g. screenshots).
 - Images which are used by the Mapper software itself
   (residing in the images folder of the mapper repository)
   are merged here in the mapper-images subtree.
