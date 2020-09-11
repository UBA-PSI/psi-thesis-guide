main.pdf: main.tex misc/setup.tex misc/titlepage.tex chapters/*.tex appendices/*.tex literature.bib
	lualatex main.tex &&  biber main && lualatex main.tex && lualatex main.tex

clean:
	latexmk -c && rm main.pdf && rm main.bbl && rm main.run.xml
move:
	if [ -d pdf ]; then \
		mv *.pdf pdf/.; \
	else \
		mkdir pdf; \
		mv *.pdf pdf/.; \
	fi
