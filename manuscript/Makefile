# Tools
LATEXMK = latexmk
RM = rm -f
PYTHON = python3

# Project-specific settings
DOCNAME = thesis
PLOTDIR = plots/
TABDIR = tables/
TEXFILES = $(wildcard *.tex)

# Targets
thesis: $(DOCNAME).pdf

# Rules
# figures:
# $(PYTHON) $(PLOTDIR)rq1_dislike_plot.py $(PLOTDIR)
# $(PYTHON) $(PLOTDIR)rq2_ad_diet.py $(PLOTDIR)
# $(PYTHON) $(PLOTDIR)rq2_cdf.py $(PLOTDIR)
# $(PYTHON) $(PLOTDIR)rq3_audience_size.py $(PLOTDIR)
# $(PYTHON) $(PLOTDIR)rq3_ages.py $(PLOTDIR)
# $(PYTHON) $(PLOTDIR)rq3_prevalence.py $(PLOTDIR)

$(DOCNAME).pdf: $(TEXFILES)
#	$(LATEXMK) -pdf -M -MP -MF $*.d $*
	latex $(DOCNAME)
	biber $(DOCNAME)
	latex $(DOCNAME)
	pdflatex $(DOCNAME).tex

allclean: clean	
	$(RM) *.pdf	
	
clean:
	$(LATEXMK) -silent -c
	$(RM) *.dvi *.aux *.bbl *.blg *.toc *.ind *.out *.brf *.ilg *.idx *.log *.soc *.d *.run.xml *.synctex.gz
	$(RM) $(DOCNAME)*.pdf
	$(LATEXMK) -silent -C

.PHONY: paper clean allclean figures diff tables

# mostly for reference, these scripts don't directly build the latex tables but print
# numbers that are used in the tables
tables:
	$(PYTHON) $(TABDIR)code_counts.py
	$(PYTHON) $(TABDIR)demographics_recruiting.py
# Table 3: analyses/rq1_dislike_reasons.Rmd

# TODO: document where the other tables are coming from

# Include auto-generated dependencies
-include *.d
