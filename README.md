
# Various tricks to make really GOOD Doxygen docs.

These include tricks on making Doxygen handle Fortran well, how to make good documentation
for Academic developers and a few other handy tricks.

## Where to look

Most of the tricks require you to put commands etc inline in your source code comments - look for the
comments tagged as DOXYHINT to find these easily. Some also require modification to the Doxyfile
and one or two need you to use a "layout" file. These files are included, and you can diff them against
the default ones Doxygen generates to see the changes. There is also a bibs file, and a sample document
to be included in the docs. Lastly, there is a custom css file to tweak some of the styling.

#The tricks

## Main Page

You can create a nice main page by, somewhere in a code file, or in a separate file, including the "\mainpage"
command and putting your text there. You can divide into sections etc. Note that \section is normally
followed by a label, then text.
If you only put one word (e.g. Introduction) it serves as both, but if you put multiple words, the first will be
assumed the label. Beware of this - it can trip you up with a few commands.


## Inline Snippets

Sometimes it is handy to have something inline in the documentation, BUT you also want to access it from somewhere
else. For instance, I have a code with command line options, and I want the description to be in a file, so I can
display it to a user, but also be in the documentation. I could copy-paste into both places, or I can put it in
a file and have Doxygen include that. I use "\verbinclude" to include the text verbatim to do this using the
formatting I put in the file. There is also an "\include" command.

## Duplicating Docs

You can duplicate docs which are common to more than one class using the "\copydoc" option. This pastes the relevant
docs inline, so you can add things like parameters after the copy. You can also use a completely dummy class if
you want some small snippet of docs which gets shared in several other places. I demo this in the C++, but in the Fortran
it is a bit flaky.


## Custom commands

You can create commands do do all sorts of things. For instance, if your project had a name you wanted to ensure
was always consistent, you could create a command for it (like you may have tried in Latex). You can also create
custom "indexes" where some text appears inline in the docs, but is also collated into a page. Doxygen
supplies 'todo' and 'bug' versions of this, as well as a page for references with the "\cite" command.

I like to do "caveats" and "future extensions" as custom tags. As well as being convenient, using an alias
means you can change the command to not output these by only changing one line instead of trying to track
down everywhere you used them. 

The 'xrefitem' command is the basis of this. The relevant commands are
copied into the example Doxyfiles, and are also in the "aliases.txt" file if you want to include them
in your own Doxyfiles.

## Custom Groups

You can also create custom "groups" or modules (not like Fortran Modules) and assign various functions into them.
These are then available collected onto a single page, as well as being documented in the normal places. For Fortran
it is good to rename the tabs Doxygen generates for clarity, using a layout file (xml). This is generated using
the command "oxygen -l layoutfilename.xml" and can then be edited.

# References
Layout file taken from https://stackoverflow.com/questions/20357342/is-there-a-way-to-change-the-doxygen-term-modules-in-the-tree-and-in-the-right-p

