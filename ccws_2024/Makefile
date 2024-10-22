# building tool
TEX = latex
BIB = bibtex
PDF = pdflatex
HTML = latex2html

# Variables
WRKDIR=tmp
PWD!=pwd
ENV=env \
    TEXINPUTS=".:${PWD}/:${PWD}/styles/:${PWD}/figures/:" \
    BIBINPUTS="${PWD}:${PWD}/styles/:" \
    BSTINPUTS=".:${PWD}/:${PWD}/styles/:"\
    LXDINPUTS=".:./styles/:./figures/:"

presentation:
	mkdir -p ${WRKDIR}
	cd ${WRKDIR}; ${ENV} ${TEX} $@
	cd ${WRKDIR}; ${ENV} ${TEX} $@
	cd ${WRKDIR}; ${ENV} ${TEX} $@
	${ENV} dvipdf -dCompatibilityLevel=1.4 -dMaxSubsetPct=100 -dSubsetFonts=true -dEmbedAllFonts=true ${WRKDIR}/$@.dvi $@.pdf

figures:
	hiearch -o figures -f eps figures/ros.yaml
	hiearch -o figures -f eps figures/buildfarm.yaml
	hiearch -o figures -f eps figures/quickie.yaml
	cd figures; dot -Teps ariles.dot > ariles.eps

# auxilary
clean:
	rm -Rf tmp

view:
	qpdfview presentation.pdf

spell:
	hunspell -t *.tex

# dummy targets
.PHONY: all clean figures

