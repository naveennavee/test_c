EXTRA_DIST = \
  clipboard-notes.txt \
  pcsc \
  wave-format-server.txt

AM_CPPFLAGS = \
  -DXRDP_CFG_PATH=\"${sysconfdir}/xrdp\" \
  -DXRDP_SBIN_PATH=\"${sbindir}\" \
  -DXRDP_SHARE_PATH=\"${datadir}/xrdp\" \
  -DXRDP_PID_PATH=\"${localstatedir}/run\" \
  -DXRDP_SOCKET_ROOT_PATH=\"${socketdir}\" \
  -I$(top_srcdir)/sesman/libsesman \
  -I$(top_srcdir)/common

CHANSRV_EXTRA_LIBS =

if XRDP_FUSE
AM_CPPFLAGS += -DXRDP_FUSE $(FUSE_CFLAGS) -DFUSE_USE_VERSION=26
CHANSRV_EXTRA_LIBS += $(FUSE_LIBS)
endif

if XRDP_FDK_AAC
AM_CPPFLAGS += -DXRDP_FDK_AAC $(FDKAAC_CFLAGS)
CHANSRV_EXTRA_LIBS += $(FDKAAC_LIBS)
endif

if XRDP_OPUS
AM_CPPFLAGS += -DXRDP_OPUS
CHANSRV_EXTRA_LIBS += -lopus
endif

if XRDP_MP3LAME
AM_CPPFLAGS += -DXRDP_MP3LAME
CHANSRV_EXTRA_LIBS += -lmp3lame
endif

if XRDP_RDPSNDAUDIN
AM_CPPFLAGS += -DXRDP_RDPSNDAUDIN
endif

AM_CFLAGS = $(X_CFLAGS)

sbin_PROGRAMS = \
  xrdp-chansrv

xrdp_chansrv_SOURCES = \
  chansrv.c \
  chansrv.h \
  chansrv_common.c \
  chansrv_common.h \
  chansrv_config.c \
  chansrv_config.h \
  chansrv_fuse.c \
  chansrv_fuse.h \
  chansrv_xfs.c \
  chansrv_xfs.h \
  clipboard.c \
  clipboard.h \
  clipboard_common.h \
  clipboard_file.c \
  clipboard_file.h \
  devredir.c \
  devredir.h \
  irp.c \
  irp.h \
  rail.c \
  rail.h \
  smartcard.c \
  smartcard.h \
  smartcard_pcsc.c \
  smartcard_pcsc.h \
  sound.c \
  sound.h \
  xcommon.c \
  xcommon.h \
  input.h \
  audin.c \
  audin.h

if XRDP_IBUS
AM_CPPFLAGS += -DXRDP_IBUS $(IBUS_CFLAGS) $(GLIB2_CFLAGS)
CHANSRV_EXTRA_LIBS += $(IBUS_LIBS) $(GLIB2_LIBS)
xrdp_chansrv_SOURCES += \
  input_ibus.c
endif


xrdp_chansrv_LDFLAGS = \
  $(X_LIBS)

xrdp_chansrv_LDADD = \
  $(top_builddir)/common/libcommon.la \
  $(top_builddir)/sesman/libsesman/libsesman.la \
  $(top_builddir)/libipm/libipm.la \
  $(X_PRE_LIBS) -lXfixes -lXrandr -lX11 $(X_EXTRA_LIBS) \
  $(CHANSRV_EXTRA_LIBS)
