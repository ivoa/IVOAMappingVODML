[![PDF-Preview](https://img.shields.io/badge/Preview-PDF-blue)](../../releases/download/auto-pdf-preview/MappingVODML-draft.pdf)
        
This repository hosts the master files of the IVOA *Mapping Data Models to VOTable* document.

The document is currently in a Working Draft stage.

The document uses [`pandoc`](http://pandoc.org) Markdown and
[`cereal`](https://github.com/olaurino/cereal) as typesetting tools.

Output documents are build in the `output` directory.

How to build the document using ceral/pandoc
============================================

In order to process the document, run the following command:

```
./cereal/bin/simple.sh *.md metadata.yaml
.\cereal\bin\simple.bat *.md .\metadata.yaml
```

This only requires `pandoc` and the `cite-proc` filter to be available in the
path. If you want to build the full HTML rendering you also need Python and the
`crossref` plugin:

```
./cereal/bin/full.sh *.md metadata.yaml
.\cereal\bin\full.bat *.md .\metadata.yaml
```

If you also have LaTeX installed you can produce a PDF:

```
./cereal/bin/pdf.sh *.md metadata.yaml
.\cereal\bin\pdf.bat *.md .\metadata.yaml
```

How to build using ivoatex
==========================
The file MappingVODML.tex is a LaTeX port of the .md files, which were going to provide a reworked mark-down version of the 
[MappingDMToVOTable-v1.0.docx](https://volute.g-vo.org/svn/!svn/bc/5630/trunk/projects/dm/vo-dml-org/doc/MappingDMtoVOTable-v1.0.docx) file.
To build it follow the description at the [ivoatex](https://github.com/ivoa-std/ivoatex) page. 

How to contribute
=================

While it is perfectly possible to collaborate using your own fork, especially
for people new to `git` it's easier to work from the same repo.

If you are comfortable with the GitHub development workflow or distributed VCS
systems in general and you prefer to
work from your fork, please feel free to do so and issue your Pull Requests from
there.

If you prefer to work on this repo directly, please ask and administrator
(e.g. @olaurino) to be added as a collaborator.

Edit files directly on GitHub
-----------------------------

You can work directly from the GitHub website if you prefer to. While this is
not recommended, it is probably possible for a repository that only contains
text documents and images, like this one. You can also upload files from your
local disk.

In GitHub, select the file you want to edit and click on the edit button in the
top right corner of the file viewport.

Start editing the document.

You can commit your changes as often as you like.

Add a commit message, and optionally an extended description.

**Please do not commit directly to `master`, but create a new branch and issue a
Pull Request, following the GitHub instructions.**

Once a new branch is created, you can keep editing files in that branch and the
Pull Request will be updated automatically.

Clone the repository
--------------------

If you want to have a local development repository and work from the command
line, please keep reading :-)

Clone the repository with:

```
$ git clone --recursive https://github.com/ivoa/mapping-vodml
$ cd mapping-vodml
```

If you are running a version of `git` that does not support the recursive
option:

```
$ git clone https://github.com/ivoa/mapping-vodml
$ cd mapping/vodml
$ git submodule init
$ git submodule update
```

Create a topic branch
---------------------

Don't work directly on the master branch. Rather, create a topic branch and then
issue a Pull Request from there.

To create a topic branch:

```
$ git checkout master
$ git pull
$ git checkout -b <branch-name>
```

Where <branch-name> is the name of the topic branch, e.g. `fix-typos` or
`rework-mapping-examples`.

When you commit you simply save changes in your local repository, so please feel
free to commit as often as you need. That is actually a good practice, because
once you have committed something the only way to lose the changes is to delete
the entire local repository.

To commit, first stage the files you want to add to the commit, and then do the
actual commit. The following code block shows some examples of `add` and
`commit` commands.

```
$ git status  # This will list the status of your working directory
$ git add 001-intro.md
$ git add .  # Stage all changes
$ git add -A . # Stage all changes, including deleted files.
$ git commit -m "short comment"
$ git commit  # In this case, the default editor will open so you can provide a\
                commit message
```

Publish your changes
--------------------

When you are happy with your changes, publish them by pushing your new commits
to the GitHub *remote*:

```
git push -u origin <branch-name>
```

The `-u` option will instruct git to start *tracking* the remote branch. The
next time you want to publish the changes you made to that branch, just use `git
push`.

Issue a Pull Request
--------------------

Pull Requests are the only mechanism for integrating changes in GitHub when
using the *Fork & Pull* development model. When working on the same repository,
Pull Requests are not required but are a good practice that allows changes to be
reviewed and discussed before they get merged.

To issue a Pull Request, in the GitHub page click on *New Pull Request*. In the
`compare` dropdown menu select the branch that contains your changes.

Write a description of your changes. People can comment on individual lines or
add generic comments. Once the Pull Request has been reviewed, it can be merged.

Depending on how many PRs are open at any time, when a PR is
merged it is possible for other PRs to have conflicts, just as local changes
might have conflicts with remote changes in trunk development.
Such conflicts are signaled by GitHub and must be resolved before
the PR can be merged.

Fetch changes from master
-------------------------

When code is merged into master, you can take the changes with the following
commands:

```
$ git checkout master
$ git fetch
$ git pull --ff-only
```

The `--ff-only` switch is recommended so that git will error if there are local
changes in the local master branch that are not also in the remote master
branch. In a topic branch development model this should never happen because
master is only updated when integrating PRs.

More info
---------

You can find more information about the GitHub workflow in the [GitHub
pages](https://guides.github.com/introduction/flow/).

Introductory git and GitHub material can be [also found on
GitHub](https://help.github.com/categories/bootcamp/)

An interactive git primer is available in the [Try Git](https://try.github.io)
pages.

Using Subversion rather than git
--------------------------------

GitHub repositories can be consumed by svn clients. This should allow developers
to use the svn command line for the git repository. Things are complicated by
the presence of git submodules.

Please refer to [this GitHub
page](https://help.github.com/articles/support-for-subversion-clients/) for
information about this support.

Pandoc info
===========

You can find documentation about the pandoc Markdown flavor in the relative
[section in the pandoc manual](http://pandoc.org/MANUAL.html#pandocs-markdown).

We also use the [`citeproc` filter](https://github.com/jgm/pandoc-citeproc) and
the [`crossref` filter](https://github.com/lierdakil/pandoc-crossref) for
citations and internal cross references.

References can be included in the `metadata.yaml` file and then cited in the
text with `[@referenceId]`, as described in the [pandoc
documentation](http://pandoc.org/MANUAL.html#citations.

