SLIDES_ROOT = root
PDFLATEX_OPTS=-file-line-error-style -interaction=nonstopmode

all: clean $(SLIDES_ROOT).pdf

check:
	chktex -n 2 -n 8 -n 6 -n 38 -n 13 -n 36 -n 24 $(SLIDES_ROOT)

clean:
	rm -f *.log *.aux *.toc *.dvi *.bbl *.blg *.*~* examples/*.*~* *.lof *.ilg *.gls *.glo *.backup *.bak.* *.nav *.out *.snm *.gif *.backup *.dat *.vrb *.brf *.fls root.pdf
	find . -name "*.aux" -delete
	find . -name "*.*~" -delete
	find . -name "*.backup" -delete

%.pdf: %.tex
	pdflatex -draftmode $(PDFLATEX_OPTS) $(SLIDES_ROOT)
	-bibtex $(SLIDES_ROOT)
	iconv --from-code=ISO-8859-1 --to-code=UTF-8 $(SLIDES_ROOT).bbl > $(SLIDES_ROOT).bbl.new
	mv $(SLIDES_ROOT).bbl.new $(SLIDES_ROOT).bbl
	pdflatex -draftmode $(PDFLATEX_OPTS) $(SLIDES_ROOT)
	pdflatex -draftmode $(PDFLATEX_OPTS) $(SLIDES_ROOT)
	pdflatex $(PDFLATEX_OPTS) $(SLIDES_ROOT)
