# resume-pandoc

LaTeX resume template for Pandoc based on Jason R. Blevins' template;
http://jblevins.org/projects/cv-template/.

I've included my own resume in markdown format as an example.
To create the LaTeX version, use:

~~~
pandoc nickconway_resume_column.md -f markdown+yaml_metadata_block \
  --template templates/conway.latex \
  -o conway-resume.tex
~~~

And to create the PDF version, use:

~~~
pandoc nickconway_resume_column.md -f markdown+yaml_metadata_block \
  --template templates/conway.latex \
  -o nick-conway-resume_2021.01.29.pdf
~~~

~~~
pandoc nickconway_resume_column_2022.09.05.md -f markdown+yaml_metadata_block \
  --template templates/conway.latex \
  -o nick-conway-resume_2022.09.05.pdf
~~~

~~~
pdflatex /Users/nick/Downloads/nick_conway_letter_template.tex -output-format=pdf
~~~

## Getting Started on MacOS

Run `brew install pandoc` to install Pandoc.

## Using Docker

Create the Docker container image using:

`docker build --tag=resume-pandoc .`

And run it using:

```
docker run --rm --volume "`pwd`:/data" --user `id -u`:`id -g` \
    resume-pandoc nickconway_resume_column.md \
                  -f markdown+yaml_metadata_block \
                  --template templates/nickconway_resume_column.latex \
                  -o nickconway_resume_column.pdf
```

For more information, please read John Bokma's blog entry [Giving Docker Desktop for macOS a Second Chance](http://johnbokma.com/blog/2021/06/02/giving-docker-desktop-for-macos-a-second-chance.html), which provides an easy walk-through.

## YAML Meta Block

name
 : the name on the resume.

keywords
 : keywords to be added to the PDF file.

left-column
 : a list of lines you want in the left column, directly under the name
   on the first page.

right-column
 : a list of lines you want in the right column, directly under the
   name on the first page.
   
fontsize
 : default `10pt`.

fontenc
 : default `T1`.

urlcolor
 : used in PDF, default `blue`.
 
linkcolor
 : used in PDF, default `magenta`.
 
numbersections
 : number sections, default off. Can also be controlled using the
 `pandoc` option `-N, --number-sections`.

name-color
 : the SVG name of the font color used for your name on the
 resume. For example `DarkSlateGray`. Note that this option
 also changes the font used for your name to bold and sans serif.

section-color
 : the SVG name of the font color used for sections. For example
 `Tomato`.  Note that this option also changes the section font to
 bold and sans serif.

Regarding the last two options: if you just want to change the font to
sans serif bold you can just use the color `black`.
