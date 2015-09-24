# Make file to compile and view latex articles
# Uses "run" to maintain functionality with Vim

FILE1=timetablef15

run:compile
	make cleanCompile

compile:$(FILE1)

$(FILE1):$(FILE1).tex
	pdflatex $(FILE1).tex
	pdflatex $(FILE1).tex

cleanCompile:
	rm -f *-blx.bib *.run.xml *.bbl *.blg *.ps *.dvi *.aux *.log *.toc *.out *~ 2> /dev/null

cleanAll: cleanCompile
	rm -f *.pdf 2> /dev/null

clean: cleanAll
