# update texdoc's documentation for the website from a fresh TL tree
# (invoked by nightly cron on tug.org)

DOC_PDF = texdoc.pdf
MAN_PDF = texdoc.man1.pdf
MAN_HTM = texdoc.man1.html

DOC_PATH = texmf/doc/texdoc
MAN_PATH = texmf/doc/man/man1
MAN_SRC = texdoc.1

all: $(DOC_PDF) $(MAN_PDF) $(MAN_HTM)

help:
	@echo 'Usage: make TLROOT=/path/to/texlive'

$(DOC_PDF): $(TLROOT)/$(DOC_PATH)/$(DOC_PDF)
	cp $< $@

$(MAN_PDF): $(TLROOT)/$(MAN_PATH)/$(MAN_PDF)
	cp $< $@

$(MAN_HTM): $(TLROOT)/$(MAN_PATH)/$(MAN_SRC)
	groff -man -Thtml $< > $@

