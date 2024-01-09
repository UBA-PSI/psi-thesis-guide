# define the tex sources to be used
SOURCES = main.tex misc/setup.tex misc/titlepage.tex $(wildcard chapters/*.tex) $(wildcard appendices/*.tex) literature.bib

# define depenencies for the docker build
DOCKERSOURCES = Dockerfile deps.txt

# this is the main target, it will compile the pdf
main.pdf: $(SOURCES)
	lualatex main.tex &&  biber main && lualatex main.tex && lualatex main.tex
	$(MAKE) move

# this target will compile the pdf in a docker container, the results will be moved to the main directory
docker: $(SOURCES) $(DOCKERSOURCES)
	# build the image
	docker build . -t build
	# run the image as container, autoremoves the container after the run
	docker run --rm -v "${PWD}:/build" --name build build
	# remove the image (will not effect cached partial images)
	docker rmi build

# remove all the files that are created during the compilation
clean:
	latexmk -c && rm -f main.pdf && rm -f main.bbl && rm -f main.run.xml

# move the pdf to the pdf directory
move:
	if [ -d pdf ]; then \
		mv *.pdf pdf/.; \
	else \
		mkdir pdf; \
		mv *.pdf pdf/.; \
	fi
