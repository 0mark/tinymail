## Process this file with automake to produce Makefile.in

camel_provider_LTLIBRARIES = libcamelsmtp.la
camel_provider_DATA = libcamelsmtp.urls

INCLUDES =					\
	-I$(top_srcdir)				\
	-I$(top_srcdir)/intl			\
	-I$(top_srcdir)/camel			\
	$(CAMEL_CFLAGS)				\
	-DTRANSDOM=\"$(GETTEXT_PACKAGE)\"	\
	-DG_LOG_DOMAIN=\"camel-smtp-provider\"

libcamelsmtp_la_SOURCES = 			\
	camel-smtp-provider.c			\
	camel-smtp-transport.c

noinst_HEADERS =			\
	camel-smtp-transport.h

libcamelsmtp_la_LDFLAGS = -avoid-version -module $(NO_UNDEFINED)

libcamelsmtp_la_LIBADD = \
	$(top_builddir)/camel/libcamel-lite-1.2.la				\
	$(CAMEL_LIBS)

EXTRA_DIST = libcamelsmtp.urls
