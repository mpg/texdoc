TARGETS = texdoc.pdf texdoc.1 texdoc.1.html texdoc.1.pdf

all: $(TARGETS)

clean: 
	@rm -f -- $(TARGETS)


texdoc.pdf: texdoc.tex
	pdflatex texdoc.tex
	pdflatex texdoc.tex

texdoc.1: texdoc ../texdoc.tlu
	help2man -N -n"finding and displaying TeX documentation"  ./$< > $@

texdoc.1.html: texdoc.1
	groff -man -Thtml $< > $@

texdoc.1.pdf: texdoc.1
	groff -man -rS11 $< | ps2pdf -sPAPERSIZE=a4 - $@
