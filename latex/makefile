all: rapport.pdf diapo.pdf

rapport.pdf: rapport.tex
	pdflatex -shell-escape rapport.tex

diapo.pdf: presentation/diapo.tex
	pdflatex -shell-escape presentation/diapo.tex	

clean:
	rm -v *.log *.out *.toc *.aux *.nav *.snm
