# OpenOrienteering Mapper User Manual

This repository is the source of the OpenOrienteering Mapper User Manual.
It is online at http://www.openorienteering.org/mapper-manual/, and
it is merged into the released software packages.
User are encouraged to contribute to this manual on Github.

## Information for contributors

[Frontpage: pages/index.md](https://github.com/OpenOrienteering/mapper-manual/blob/gh-pages/pages/index.md)

Contributors may submit pull requests or ask to be added as a collaborator for this repository.
 
Pages may be edited directly on Github. Github's online editor even features a preview.

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

## Information for maintainers

The following assumes that 
 - you are working in the mapper-manual repository
   (i.e. git remote "origin" points to the mapper-manual repository on Github),
 - you added another git remote "mapper" which points to the mapper repository on Github,
 - you fetched the master branch from the mapper repository,
 - you configured a local branch "master" for the mapper repository.

The initial setup could look like this:

~~~
git clone -b gh-pages https://github.com/OpenOrienteering/mapper-manual.git
cd mapper-manual
git remote add mapper https://github.com/OpenOrienteering/mapper.git
git fetch mapper master
git branch master mapper/master
~~~

### Merging the images from Mapper to the manual

The images used by Mapper are maintained in the images directory of the mapper repository.
The mapper-manual gh-pages branch has a copy of these images in the mapper-images subtree.
To update this copy, ```git subtree``` needs to be invoked twice.
The git history is maintained in the mapper master branch, so we can squash all changes.

1. Split the images out of the mapper master branch into the mapper images branch:
   
   ~~~
   git fetch mapper images
   git checkout master
   git pull master
   git subtree split -P images -b images --squash
   git push mapper images:images
   ~~~
   
2. Pull the images into the mapper-images subtree of the mapper-manual gh-pages branch:
   
   ~~~
   git checkout gh-pages
   git pull gh-pages
   git subtree pull -P mapper-images --squash mapper images
   git push
   ~~~
   
### Merging the pages from the manual repository to Mapper

The contents of the manual are maintained in the pages directory of this repository.
The mapper repository master branch has a copy of these pages in the doc/manual/pages subtree.
To update that copy, ```git subtree``` needs to be invoked twice.
The git history is maintained in this repository's gh-pages branch, so we can squash all changes.

The following assumes that you are working in the mapper-manual repository
(i.e. git remote "origin" points to the mapper-manual repository on Github),
and you add another git remote "mapper" which points to the mapper repository on Github.

1. Push the pages out of this repository's gh-pages branch into the mapper manual branch:
   
   ~~~
   git fetch mapper manual
   git checkout gh-pages
   git pull
   git subtree push -P pages --squash mapper manual
   ~~~
   
2. Pull the pages into the doc/manual/pages subtree of the mapper master branch:
   
   ~~~
   git checkout master
   git pull
   git subtree pull -P doc/manual/pages --squash origin manual
   ~~~
   
   Use "Merge updated manual pages subtree" as commit message.

3. Check that Mapper builds without errors for ```doc/manual```. Check the resulting manual. Really do that. Only when everything goes well, push the changes:

   ~~~
   git push
   ~~~
   
