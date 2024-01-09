SOURCES = main.tex misc/setup.tex misc/titlepage.tex $(wildcard chapters/*.tex) $(wildcard appendices/*.tex) literature.bib
DOCKERFILES = Dockerfile deps.txt

main.pdf: $(SOURCES)
	lualatex main.tex &&  biber main && lualatex main.tex && lualatex main.tex

docker: $(SOURCES) $(DOCKERSOURCES)
	docker build . -t build
	docker run --rm -v "${PWD}:/build" --name build build

clean:
	latexmk -c && rm -f main.pdf && rm -f main.bbl && rm -f main.run.xml
move:
	if [ -d pdf ]; then \
		mv *.pdf pdf/.; \
	else \
		mkdir pdf; \
		mv *.pdf pdf/.; \
	fi
