TARGETS = texdoc.pdf texdoc.1 texdoc.man1.pdf
AUX = texdoc.aux texdoc.log texdoc.out

all: $(TARGETS)

texdoc.pdf: texdoc.tex
	xelatex --interaction=batchmode $< >/dev/null
	xelatex --interaction=batchmode $< >/dev/null

texdoc.1: texdoc ../script/constants.tlu Makefile
	help2man -N -n"find & view documentation in TeX Live" ./$< > $@

texdoc.man1.html: texdoc.1
	groff -man -Thtml $< > $@

texdoc.man1.pdf: texdoc.1
	groff -man -rS11 $< | ps2pdf -sPAPERSIZE=a4 - $@

mrproper: clean
	@rm -f -- $(TARGETS)

clean: 
	@rm -f -- $(AUX)

.PHONY: clean mrproper
