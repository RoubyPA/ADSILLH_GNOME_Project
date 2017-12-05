all: rapport diapo

rapport: rapport.tex
	pdflatex -shell-escape rapport.tex

diapo: presentation/diapo.tex
	make -C presentation -f diapo.makefile

clean:
	rm -v *.log *.out *.toc *.aux 
	make -C presentation -f diapo.makefile clean
