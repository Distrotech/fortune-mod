
COOKIES=art ascii-art computers cookie definitions drugs education ethnic \
	food fortunes goedel humorists kids law linuxcookie literature \
	love magic medicine men-women miscellaneous news people pets \
	platitudes politics riddles science songs-poems sports \
	startrek translate-me wisdom work zippy

STRFILE=../util/strfile

.PHONY: all cookies o-cookies w-cookies install clean

all: cookies o-cookies w-cookies

cookies: cookies-stamp

o-cookies:
	if [ $(OFFENSIVE) = 1 ] ; then \
	    cd off && $(MAKE) OCOOKIEDIR=$(OCOOKIEDIR) ; fi

w-cookies:
	if [ $(WEB) = 1 ] ; then \
	    cd html && $(MAKE) WCOOKIEDIR=$(WCOOKIEDIR); fi

cookies-stamp:
	rm -f *.dat
	for i in $(COOKIES) ; do $(STRFILE) $$i || exit $? ; done
	touch cookies-stamp

install: cookies-stamp
	install -m 0755 -d $(COOKIEDIR)
	if [ $(OFFENSIVE) = 1 ] ; then cd off && $(MAKE) install ; fi
	if [ $(WEB) = 1 ] ; then cd html && $(MAKE) install ; fi
	for i in $(COOKIES) ; do \
		install -m 0644 $$i $$i.dat $(COOKIEDIR) || exit $? ; done

clean:
	rm -f cookies-stamp *.dat
	cd off && $(MAKE) clean
	cd html && $(MAKE) clean
