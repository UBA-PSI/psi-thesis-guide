main.pdf: main.tex
	lualatex main.tex && lualatex main.tex && biber main && lualatex main.tex

clean:
	latexmk -c && rm main.bbl && rm main.run.xml

move:
	if [ -d pdf ]; then \
		mv *.pdf pdf/.; \
	else \
		mkdir pdf; \
		mv *.pdf pdf/.; \
	fi
