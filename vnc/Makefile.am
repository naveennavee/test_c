AM_CPPFLAGS = \
  -DXRDP_CFG_PATH=\"${sysconfdir}/xrdp\" \
  -DXRDP_SBIN_PATH=\"${sbindir}\" \
  -DXRDP_SHARE_PATH=\"${datadir}/xrdp\" \
  -DXRDP_PID_PATH=\"${localstatedir}/run\" \
  -I$(top_srcdir)/common

AM_CFLAGS = $(X_CFLAGS)

module_LTLIBRARIES = \
  libvnc.la

libvnc_la_SOURCES = \
  vnc.c \
  vnc_clip.c \
  rfb.c \
  vnc.h \
  vnc_clip.h \
  rfb.h

libvnc_la_LIBADD = \
  $(top_builddir)/common/libcommon.la

if !MACOS
libvnc_la_LDFLAGS = -avoid-version -module
endif
