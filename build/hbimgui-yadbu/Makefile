PKGNAME = hbimgui-yadbu
PKGVER  = 20250713
PKGBLD  = +alcz
DEPENDS = harbour-core hbimgui-docking

TOPDIR  = ../..
include $(TOPDIR)/common.mk
include $(TOPDIR)/pmgr.mk

WORKDIR = harbour-cimgui-sokol-starterkit-master
SOURCES = harbour-cimgui@master.tar.gz
SRCURL  = https://github.com/alcz/harbour-cimgui-sokol-starterkit/archive/refs/heads
EXTRDIR = harbour-cimgui-sokol-starterkit-master/examples

include $(TOPDIR)/hbarch.mk

include $(TOPDIR)/hbinfo.mk

do-fetch: std-fetch
do-extract: std-extract
do-patch: #fix-configure

do-config:

do-build:
# contrib/cimgui vs. contrib/cimgui-docking duo is messy ...
# TODO: add zig|clang to request -lstdc++ upstream
	-mv $(PKGDEST)/harbour/contrib/cimgui $(PKGDEST)/harbour/contrib/cimgui.bk
	cd $(WORKDIR)/examples && IMGUI_DOCKING=y $(HBMK) yadbu.hbp -lstdc++ $(PKGDEST)/harbour/contrib/cimgui-docking/cimgui.hbc
	-mv $(PKGDEST)/harbour/contrib/cimgui.bk $(PKGDEST)/harbour/contrib/cimgui

do-pkginst:
#	mkdir -p dest/lib && cp lib*.a dest/lib
	mkdir -p dest/harbour/contrib
	mkdir -p dest/bin
	cp -r $(WORKDIR)/examples/yadbu$(_EXT) dest/bin
