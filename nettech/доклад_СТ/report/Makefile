REPORT      = report.md
TITLE_TEX   = title.tex
TITLE_MD    = title.md
FILTERS     = --filter pandoc-crossref
OPTIONS     = --standalone
PDF_ENGINE  = --pdf-engine=xelatex
FROM_OPT    = --from=markdown+gfm_auto_identifiers
MAINFONT    = -V mainfont="Liberation Serif"
MONOFONT    = -V monofont="Liberation Mono"
GEOMETRY    = -V geometry:"top=20mm, bottom=20mm, left=30mm, right=15mm"
HEADER      = -V header-includes='\usepackage{graphicx}\usepackage{xcolor}'

all: report.pdf report.docx report.qmd

# PDF: LaTeX-титульник подключается через include-before-body
report.pdf: $(REPORT) $(TITLE_TEX)
	pandoc "$(REPORT)" $(FILTERS) $(FROM_OPT) $(PDF_ENGINE) $(OPTIONS) \
		$(GEOMETRY) $(HEADER) $(MAINFONT) $(MONOFONT) \
		--include-before-body="$(TITLE_TEX)" \
		-o report.pdf

# DOCX: markdown-титульник склеивается с основным файлом
report.docx: $(REPORT) $(TITLE_MD)
	pandoc "$(TITLE_MD)" "$(REPORT)" $(FILTERS) $(FROM_OPT) $(OPTIONS) -o report.docx

# QMD: аналогично DOCX
report.qmd: $(REPORT) $(TITLE_MD)
	pandoc "$(TITLE_MD)" "$(REPORT)" $(FILTERS) $(FROM_OPT) $(OPTIONS) -t markdown -o report.qmd

clean:
	rm -f report.pdf report.docx report.qmd

.PHONY: all clean
