TARGETS = texdoc.pdf texdoc.1 texdoc.1.html texdoc.1.pdf
AUX = texdoc.aux texdoc.log texdoc.out

all: $(TARGETS)

texdoc.pdf: texdoc.tex
	pdflatex --interaction=batchmode $< >/dev/null
	pdflatex --interaction=batchmode $< >/dev/null

texdoc.1: texdoc ../texdoc.tlu Makefile
	help2man -N -n"finding & viewing TeX documentation"  ./$< > $@

texdoc.1.html: texdoc.1
	groff -man -Thtml $< > $@

texdoc.1.pdf: texdoc.1
	groff -man -rS11 $< | ps2pdf -sPAPERSIZE=a4 - $@

mrproper: clean
	@rm -f -- $(TARGETS)

clean: 
	@rm -f -- $(AUX)

.PHONY: clean mrproper
