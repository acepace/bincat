ifdef PREFIX
PREFIXOPT = --prefix=$(PREFIX)
endif

ifdef DESTDIR
DESTDIROPT = --root=$(DESTDIR)
endif

all:
	python2 ./setup.py build

install:
	python2 ./setup.py install $(PREFIXOPT) $(DESTDIROPT)

doc:
	make -C doc generate
	make -C doc html
	make -C doc latexpdf

copydoc: checkenv doc
	mkdir -p $(DOCPATH)
	cp doc/build/latex/BinCAT.pdf $(DOCPATH)
	cp -r doc/build/html $(DOCPATH)

clean:
	rm -rf build
	make -C doc clean

checkenv:
ifndef DOCPATH
	$(error DOCPATH is not set)
endif

.PHONY: install clean doc copydoc checkenv
