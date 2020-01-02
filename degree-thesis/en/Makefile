main.pdf: main.tex Misc/setup.tex Misc/titlepage.tex Chapters/*.tex Appendices/*.tex
	lualatex main.tex && lualatex main.tex && biber main && lualatex main.tex

clean:
	latexmk -c && rm main.pdf && rm main.bbl && rm main.run.xml
move:
	if [ -d pdf ]; then \
		mv *.pdf pdf/.; \
	else \
		mkdir pdf; \
		mv *.pdf pdf/.; \
	fi
