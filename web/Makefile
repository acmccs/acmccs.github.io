###
### This Makefile is for making the website only!
###

GITHUB_PAGES_BRANCH=gh-pages
THEME = ccs

MARKDOWN = python3 -m markdown
BASEDIR = .
SRCDIR = ~/ccs2017/accepts
LATEXDIR = $(BASEDIR)/../latex
DOCSDIR = $(BASEDIR)/content/docs
PAGEDIR = $(BASEDIR)/content/
LATEXIFY = python3 $(LATEXDIR)/utils/latexify.py

html:
	cd $(SRCDIR); python3 process.py
	cat $(SRCDIR)/papers.top $(SRCDIR)/sessions.html $(SRCDIR)/papers.bottom > $(PAGEDIR)/sessions.md
	cd $(SRCDIR); for f in session[??].html
		cat $(SRCDIR)/papers.top $f $(SRCDIR)/papers.bottom > $(PAGEDIR)/$f.md
		done
	cat $(SRCDIR)/papers.top $(SRCDIR)/papers.html $(SRCDIR)/papers.bottom > $(PAGEDIR)/papers.md
	cat $(SRCDIR)/papers.top $(SRCDIR)/openpapers.html $(SRCDIR)/papers.bottom > $(PAGEDIR)/openpapers.md
	cat $(SRCDIR)/papers.top $(SRCDIR)/artifacts.html $(SRCDIR)/papers.bottom > $(PAGEDIR)/artifacts.md
	cat $(SRCDIR)/papers.top $(SRCDIR)/authors.html $(SRCDIR)/papers.bottom > $(PAGEDIR)/authors.md
	cat $(SRCDIR)/papers.top $(SRCDIR)/institutions.html $(SRCDIR)/papers.bottom > $(PAGEDIR)/institutions.md
	hugo --theme=$(THEME)

develop:
	make html
	hugo server --theme=$(THEME) --buildDrafts --watch

github: html
	cp -r public/* ../
	git add -A; git commit -m "Rebuilt site" ; git push

.PHONY: html clean develop
