REPORT = report.md
FILTERS = --filter pandoc-crossref
OPTIONS = --standalone
PDF_ENGINE = --pdf-engine=xelatex
FROM_OPT = --from=markdown+gfm_auto_identifiers
MAINFONT = -V mainfont="Liberation Serif"
MONOFONT = -V monofont="Liberation Mono"
GEOMETRY = -V geometry:"top=20mm, bottom=20mm, left=30mm, right=15mm"
HEADER = -V header-includes='\usepackage{graphicx}\usepackage{xcolor}'

all: report.pdf report.docx report.qmd

report.pdf: $(REPORT)
	pandoc "$(REPORT)" $(FILTERS) $(FROM_OPT) $(PDF_ENGINE) $(OPTIONS) $(GEOMETRY) $(HEADER) $(MAINFONT) $(MONOFONT) -o report.pdf

report.docx: $(REPORT)
	pandoc "$(REPORT)" $(FILTERS) $(FROM_OPT) $(OPTIONS) -o report.docx

report.qmd: $(REPORT)
	pandoc "$(REPORT)" $(FILTERS) $(FROM_OPT) $(OPTIONS) -t markdown -o report.qmd

clean:
	rm -f report.pdf report.docx report.qmd

.PHONY: all clean
