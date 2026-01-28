PKGNAME = hbimgui$(HBPK_NAME_SUFFIX)
PKGVER  = 20250713
PKGBLD  = +alcz
DEPENDS = harbour-core

TOPDIR  = ../..
include $(TOPDIR)/common.mk
include $(TOPDIR)/pmgr.mk

WORKDIR = harbour-cimgui-sokol-starterkit-master
SOURCES = harbour-cimgui@master.tar.gz
SRCURL  = https://github.com/alcz/harbour-cimgui-sokol-starterkit/archive/refs/heads

include $(TOPDIR)/hbarch.mk

include $(TOPDIR)/hbinfo.mk

do-fetch: std-fetch
do-extract: std-extract
do-patch: #fix-configure

do-config:

do-build:
	cd $(WORKDIR) && $(HBMK) meta-rebuild$(HBPK_NAME_SUFFIX).hbp

do-pkginst:
#	mkdir -p dest/lib && cp lib*.a dest/lib
	mkdir -p dest/harbour/contrib
	mkdir -p dest/harbour/lib/$(HBPK_PLATFORM)/$(HBPK_COMPILER)
	mkdir -p dest/bin
	cp -r $(WORKDIR)/cimplot dest/harbour/contrib/
	cp -r $(WORKDIR)/cimgui$(HBPK_NAME_SUFFIX) dest/harbour/contrib/
	cp -r $(WORKDIR)/cimgui-common dest/harbour/contrib/
	cp -r $(WORKDIR)/sokol dest/harbour/contrib/
	cp -r $(WORKDIR)/hexeterminal dest/harbour/contrib/
	cp -r $(WORKDIR)/images dest/harbour/contrib/
	cp -r $(WORKDIR)/examples dest/harbour/contrib/cimgui-examples
	cp -r $(WORKDIR)/examples/fonts dest/bin/
	cp -r $(WORKDIR)/examples/OpenSans-Regular.ttf dest/bin/
