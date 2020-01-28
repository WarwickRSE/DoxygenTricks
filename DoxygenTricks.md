
# Various tricks to make really GOOD Doxygen docs.


## Main Page

You can create a nice main page by, somewhere in a code file, or in a separate file, including the "\mainpage" command and putting your text there. You can divide into sections etc. Note that \section is normally followed by a label, then text. If you only put one word (e.g. Introduction) it serves as both, but if you put multiple words, the first will be assumed the label. Beware of this. 


## Inline Snippets

Sometimes it is handy to have something inline in the documentation, BUT you also want to access it from somewhere else. For instance, I have a code with command line options, and I want the description to be in a file, so I can display it to a user, but also be in the documentation. I could copy-paste into both places, or I can put it in a file and have Doxygen include that. I use "\verbinclude" to include the text verbatim to do this. 

## Custom commands

You can create commands do do all sorts of things. For instance, if your project had a name you wanted to ensure was always consistent, you could create a command for it (like you may have tried in Latex). You can also create custom "indexes" where some text appears inline in the docs, but is also collated into a page. Doxygen supplies 'todo' and 'bug' versions of this, as well as a page for references. 

I like to do "caveats" and "future extensions" as custom tags. As well as being convenient, using an alias means you can change the command to not output these by only changing one line instead of trying to track down everywhere you used them. 

The 'xrefitem' command is the basis of this, given in the aliases file. Stick the contents of this in your doxyfile somewhere. 

## Custom Groups

You can also create custom "groups" or modules (not like Fortran Modules) and assign various functions to them. 

# The Fortran and Cpp directories contain some example code with an assortment of useful Doxygen. The interesting parts are
marked with DOXYHINT in a (language appropriate) comment, just before the relevant Doxygen

# References
Layout file taken from https://stackoverflow.com/questions/20357342/is-there-a-way-to-change-the-doxygen-term-modules-in-the-tree-and-in-the-right-p

