% MARKDOWN2PDF(1) Pandoc User Manuals
% John MacFarlane and Recai Oktas
% January 8, 2008

# NAME

markdown2pdf - converts markdown-formatted text to PDF, using pdflatex 

# SYNOPSIS

markdown2pdf [*options*] [*input-file*]...

# DESCRIPTION

`markdown2pdf` converts *input-file* (or text from standard 
input) from markdown-formatted plain text to PDF, using `pandoc`
and `pdflatex`. If no output filename is specified (using the `-o`
option), the name of the output file is derived from the input file;
thus, for example, if the input file is *hello.txt*, the output file
will be *hello.pdf*. If the input is read from STDIN and no output
filename is specified, the output file will be named *stdin.pdf*. If
multiple input files are specified, they will be concatenated before
conversion, and the name of the output file will be derived from the
first input file.

Input is assumed to be in the UTF-8 character encoding.  If your
local character encoding is not UTF-8, you should pipe input
through `iconv`:

    iconv -t utf-8 input.txt | markdown2pdf

`markdown2pdf` assumes that the `unicode`, `array`, `fancyvrb`,
`graphicx`, and `ulem` packages are in latex's search path. If these
packages are not included in your latex setup, they can be obtained from
<http://ctan.org>.

# OPTIONS

-o *FILE*, \--output=*FILE*
:   Write output to *FILE*.

\--strict
:   Use strict markdown syntax, with no extensions or variants.

\--xetex
:   Use xelatex instead of pdflatex to create the PDF.

-N, \--number-sections
:   Number section headings in LaTeX output.  (Default is not to number them.)

\--template=*FILE*
:   Use *FILE* as a custom template for the generated document. Implies
    `-s`. See the section TEMPLATES in `pandoc`(1) for information about
    template syntax.  Use `pandoc -D latex` to print the default LaTeX
    template.

-V KEY=VAL, \--variable=*KEY:VAL*
:   Set the template variable KEY to the value VAL when rendering the
    document in standalone mode. This is only useful when the
    `--template` option is used to specify a custom template, since
    pandoc automatically sets the variables used in the default
    templates.

-H *FILE*, \--include-in-header=*FILE*
:   Include (LaTeX) contents of *FILE* at the end of the header.  Implies
    `-s`.

-B *FILE*, \--include-before-body=*FILE*
:   Include (LaTeX) contents of *FILE* at the beginning of the document body.

-A *FILE*, \--include-after-body=*FILE*
:   Include (LaTeX) contents of *FILE* at the end of the document body.

-C *FILE*, \--custom-header=*FILE*
:   Use contents of *FILE* as the document header. *Note: This option is
    deprecated. Users should transition to using `--template` instead.*

# SEE ALSO

`pandoc`(1), `pdflatex`(1)
