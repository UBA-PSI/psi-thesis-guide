main.pdf: main.tex
	lualatex main.tex && lualatex main.tex && biber main && lualatex main.tex

clean: move
	latexmk -c

move:
	if [ -d pdf ]; then \
		mv *.pdf pdf/.; \
	else \
		mkdir pdf; \
		mv *.pdf pdf/.; \
	fi
