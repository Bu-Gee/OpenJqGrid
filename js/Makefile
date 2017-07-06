.PHONY: all

all: minified/jquery.jqGrid.min.js jquery.jqGrid.js

minified/jquery.jqGrid.min.js: jquery.jqGrid.js
	java -jar ../closure-compiler/compiler.jar \
	    --create_source_map minified/jquery.jqGrid.map.js \
	    --js_output_file minified/jquery.jqGrid.min.js \
	    --js jquery.jqGrid.js 

SRCS=grid.base.js grid.celledit.js grid.common.js grid.custom.js grid.filter.js grid.formedit.js grid.grouping.js grid.import.js grid.inlinedit.js grid.jqueryui.js grid.pivot.js grid.subgrid.js grid.tbltogrid.js grid.treegrid.js jqDnR.js jqModal.js jquery.fmatter.js JsonXml.js

jquery.jqGrid.js: $(SRCS)
	rm -f $@
	for i in $(SRCS); do \
	    echo $$i; \
	    echo -e "\n//\n// Imported from $$i\n//" >> $@; \
	    cat $$i | sed 's/\r$$//' >> $@; \
	    echo "" >> $@; \
	done
