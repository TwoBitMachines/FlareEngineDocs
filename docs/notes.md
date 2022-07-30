

choose to seperate source and build, y
rename build folder as docs and go to make.bat and makefile and change build name to docs there too.

use perl command line, not regular cmd, to use latex and generate pdf

latexmk -pdf or just latexmk (have to be in folder where .tex file exists)

.\make html
.\docs\html\index.html