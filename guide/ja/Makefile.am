figdir = figures
docname = gnucash-guide
lang = ja_JP
fopconfig = fop.xconf
omffile = $(docname)-ja_JP.omf
entities = \
	fdl-appendix.xml \
	legal.xml \
	ch_oview.xml \
	ch_basics.xml \
	ch_accts.xml \
	ch_txns.xml \
	ch_cbook.xml \
	ch_cc.xml \
	ch_loans.xml \
	ch_invest.xml \
	ch_capgain.xml \
	ch_currency.xml \
	ch_dep.xml \
	ch_bus_ar.xml \
	ch_bus_ap.xml \
	ch_bus_pay.xml \
	ch_budgets.xml \
	ch_oth_assets.xml \
	ch_python_bindings.xml \
	appendixa.xml \
	appendixb.xml \
	appendixc.xml \
	appendixd.xml
DISTCLEANFILES =  $(docname)-ja_JP.omf.out mincho.xml gothic.xml $(fopconfig)
CLEANFILES =  $(DISTCLEANFILES)
FOPFLAGS = -l $(lang) -c $(fopconfig)
XSLTFLAGS_FO= --stringparam paper.type A4
include $(top_srcdir)/xmldocs.make
if WITH_JAPANESE_PDF
include $(top_srcdir)/pdf.make
endif
include $(top_srcdir)/epub.make
if WITH_MOBI
include $(top_srcdir)/mobi.make
endif

if WITH_JAPANESE_PDF
mincho.xml: @JAPANESE_MINCHO_TTF@
	$(FOP_TTFREADER) $< $@

gothic.xml: @JAPANESE_GOTHIC_TTF@
	$(FOP_TTFREADER) $< $@

$(docname).pdf: $(docname).fo mincho.xml gothic.xml $(fopconfig)
	$(FOP) $(FOPFLAGS) -fo $(docname).fo -pdf $@
else
$(docname).pdf:
endif
