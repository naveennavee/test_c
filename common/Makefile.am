if XRDP_PIXMAN
  PIXMAN_SOURCES =
else
  PIXMAN_SOURCES = pixman-region16.c pixman-region.h
endif

EXTRA_DIST = pixman-region.c

include_HEADERS = \
  ms-erref.h \
  ms-fscc.h \
  ms-rdpbcgr.h \
  ms-rdpeclip.h \
  ms-rdpefs.h \
  ms-rdpegdi.h \
  ms-rdpele.h \
  ms-rdperp.h \
  ms-rdpedisp.h \
  ms-smb2.h \
  xrdp_client_info.h \
  xrdp_constants.h \
  xrdp_rail.h \
  xrdp_scancode_defs.h \
  xrdp_sockets.h

AM_CPPFLAGS = \
  -DXRDP_CFG_PATH=\"${sysconfdir}/xrdp\" \
  -DXRDP_SBIN_PATH=\"${sbindir}\" \
  -DXRDP_SHARE_PATH=\"${datadir}/xrdp\" \
  -DXRDP_PID_PATH=\"${localstatedir}/run\" \
  -DXRDP_LOG_PATH=\"${localstatedir}/log\"

# -no-suppress is an automake-specific flag which is needed
# to prevent us missing compiler errors in some circumstances
# (see https://github.com/neutrinolabs/xrdp/pull/1843 )
AM_CFLAGS = -no-suppress $(OPENSSL_CFLAGS)

module_LTLIBRARIES = \
  libcommon.la

libcommon_la_SOURCES = \
  arch.h \
  base64.h \
  base64.c \
  defines.h \
  fifo.c \
  fifo.h \
  file.c \
  file.h \
  guid.c \
  guid.h \
  list.c \
  list.h \
  list16.c \
  list16.h \
  log.c \
  log.h \
  os_calls.c \
  os_calls.h \
  parse.c \
  parse.h \
  rail.h \
  scancode.c \
  scancode.h \
  ssl_calls.c \
  ssl_calls.h \
  string_calls.c \
  string_calls.h \
  thread_calls.c \
  thread_calls.h \
  trans.c \
  trans.h \
  unicode_defines.h \
  $(PIXMAN_SOURCES)

libcommon_la_LIBADD = \
  -lpthread \
  $(OPENSSL_LIBS) \
  $(DLOPEN_LIBS)
