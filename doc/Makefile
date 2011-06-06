TARGETS = texdoc.pdf texdoc.1 texdoc.man1.pdf
AUX = texdoc.aux texdoc.log texdoc.out

H2M_NAME = "find & view documentation in TeX Live"
H2M_INC = include.h2m
H2M_SOURCES = ../script/constants.tlu ../script/texdoc.tlu

all: $(TARGETS)

texdoc.pdf: texdoc.tex
	xelatex --interaction=batchmode $< >/dev/null
	xelatex --interaction=batchmode $< >/dev/null

texdoc.1: texdoc Makefile $(H2M_INC) $(H2M_SOURCES)
	../tools/sh -- help2man -N -n$(H2M_NAME) --include $(H2M_INC) ./$< > $@

texdoc.man1.html: texdoc.1
	groff -man -Thtml $< > $@

texdoc.man1.pdf: texdoc.1
	groff -man -rS11 $< | ps2pdf -sPAPERSIZE=a4 - $@

mrproper: clean
	@rm -f -- $(TARGETS)

clean: 
	@rm -f -- $(AUX)

.PHONY: clean mrproper
