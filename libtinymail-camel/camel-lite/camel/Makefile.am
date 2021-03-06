SUBDIRS = . providers

AM_CFLAGS = -fPIC

if OS_WIN32
LIBCAMEL_PLATFORM_DEP_SOURCES = camel-win32.c
LIBCAMEL_PROVIDER_PLATFORM_DEP_SOURCES =
else
LIBCAMEL_PLATFORM_DEP_SOURCES = \
	camel-lock-client.c \
	camel-stream-process.c
LIBCAMEL_PROVIDER_PLATFORM_DEP_SOURCES =	\
	camel-movemail.c			\
	camel-sasl-kerberos4.c
endif

camel-lite-$(API_VERSION).pc:camel-lite.pc
	cp $< $@

camel-lite-provider-$(API_VERSION).pc:camel-lite-provider.pc
	cp $< $@

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_in_files = camel-lite.pc.in camel-lite-provider.pc.in
pkgconfig_DATA = $(pkgconfig_in_files:.pc.in=-$(API_VERSION).pc)

libcamel_liteincludedir = $(includedir)/camel-lite/camel
libcamel_lite_providerincludedir = $(includedir)/camel-lite/camel
camel_litelibexecdir = $(libexecdir)

# noinst_LTLIBRARIES = libcamel-lite-1.2.la
lib_LTLIBRARIES = libcamel-lite-1.2.la

INCLUDES = -I.. -I$(srcdir)/.. \
	-I$(top_srcdir)/intl \
	-DCAMEL_LIBEXECDIR=\""$(camel_litelibexecdir)"\" \
	-DCAMEL_PROVIDERDIR=\""$(camel_lite_providerdir)"\" \
	-DG_LOG_DOMAIN=\"camel-lite\" \
	-DTRANSDOM=\"$(GETTEXT_PACKAGE)\" \
	-DE_DATA_SERVER_PREFIX=\"$(prefix)\" \
	-DLOCALEDIR=\""$(localedir)"\" \
	$(CAMEL_CFLAGS)

provider_sources = 	\
	camel-cipher-context.c			\
	camel-digest-folder.c			\
	camel-digest-store.c			\
	camel-digest-summary.c			\
	camel-disco-diary.c			\
	camel-disco-folder.c			\
	camel-disco-store.c			\
	camel-filter-driver.c			\
	camel-filter-search.c			\
	camel-folder-search.c			\
	camel-folder-summary.c			\
	camel-folder-thread.c			\
	camel-folder.c				\
	camel-gpg-context.c			\
	camel-http-stream.c			\
	camel-offline-folder.c			\
	camel-offline-journal.c			\
	camel-offline-store.c			\
	camel-provider.c			\
	camel-sasl-anonymous.c			\
	camel-sasl-cram-md5.c			\
	camel-sasl-digest-md5.c			\
	camel-sasl-gssapi.c			\
	camel-sasl-login.c			\
	camel-sasl-ntlm.c			\
	camel-sasl-plain.c			\
	camel-sasl-popb4smtp.c			\
	camel-sasl.c				\
	camel-search-private.c			\
	camel-service.c				\
	camel-session.c				\
	camel-smime-context.c			\
	camel-store-summary.c			\
	camel-store.c				\
	camel-tcp-stream-raw.c			\
	camel-tcp-stream.c			\
	camel-transport.c			\
	camel-uid-cache.c			\
	camel-vee-folder.c			\
	camel-vee-store.c			\
	camel-vee-summary.c			\
	camel-vtrash-folder.c			\
	$(LIBCAMEL_PROVIDER_PLATFORM_DEP_SOURCES)

if ENABLE_OPENSSL
provider_sources += camel-tcp-stream-openssl.c
else
provider_sources += camel-tcp-stream-ssl.c
endif

providerinclude_headers =		\
	camel-cipher-context.h			\
	camel-digest-folder.h			\
	camel-digest-store.h			\
	camel-digest-summary.h			\
	camel-disco-diary.h			\
	camel-disco-folder.h			\
	camel-disco-store.h			\
	camel-filter-driver.h			\
	camel-filter-search.h			\
	camel-folder-search.h			\
	camel-folder-summary.h			\
	camel-folder-thread.h			\
	camel-folder.h				\
	camel-gpg-context.h			\
	camel-http-stream.h			\
	camel-html-parser.h			\
	camel-iconv.h				\
	camel-lock-helper.h			\
	camel-movemail.h			\
	camel-news-address.h			\
	camel-offline-folder.h			\
	camel-offline-journal.h			\
	camel-offline-store.h			\
	camel-process.h				\
	camel-provider.h			\
	camel-sasl-anonymous.h			\
	camel-sasl-cram-md5.h			\
	camel-sasl-digest-md5.h			\
	camel-sasl-gssapi.h			\
	camel-sasl-kerberos4.h			\
	camel-sasl-login.h			\
	camel-sasl-ntlm.h			\
	camel-sasl-plain.h			\
	camel-sasl-popb4smtp.h			\
	camel-sasl.h				\
	camel-service.h				\
	camel-session.h				\
	camel-smime-context.h			\
	camel-store-summary.h			\
	camel-store.h				\
	camel-tcp-stream-raw.h			\
	camel-tcp-stream-ssl.h			\
	camel-tcp-stream.h			\
	camel-transport.h			\
	camel-uid-cache.h			\
	camel-vee-folder.h			\
	camel-vee-store.h			\
	camel-vee-summary.h			\
	camel-vtrash-folder.h

libcamel_lite_1_2_la_SOURCES = 			\
	$(provider_sources)			\
	broken-date-parser.c			\
	camel-address.c				\
	camel-arg.c				\
	camel-block-file.c			\
	camel-charset-map.c			\
	camel-data-cache.c			\
	camel-data-wrapper.c			\
	camel-debug.c				\
	camel-exception.c			\
	camel-file-utils.c			\
	camel-html-parser.c			\
	camel-index.c				\
	camel-internet-address.c		\
	camel-junk-plugin.c			\
	camel-list-utils.c			\
	camel-lock.c				\
	camel-medium.c				\
	camel-mime-filter-basic.c		\
	camel-mime-filter-bestenc.c		\
	camel-mime-filter-canon.c		\
	camel-mime-filter-charset.c		\
	camel-mime-filter-crlf.c		\
	camel-mime-filter-enriched.c		\
	camel-mime-filter-from.c		\
	camel-mime-filter-gzip.c		\
	camel-mime-filter-html.c		\
	camel-mime-filter-index.c		\
	camel-mime-filter-linewrap.c		\
	camel-mime-filter-pgp.c			\
	camel-mime-filter-save.c		\
	camel-mime-filter-tohtml.c		\
	camel-mime-filter-windows.c		\
	camel-mime-filter-yenc.c		\
	camel-mime-filter.c			\
	camel-mime-message.c			\
	camel-mime-parser.c			\
	camel-mime-part-utils.c			\
	camel-mime-part.c			\
	camel-mime-utils.c			\
	camel-mime-tables.c			\
	camel-multipart-encrypted.c		\
	camel-multipart-signed.c		\
	camel-multipart.c			\
	camel-net-utils.c			\
	camel-nntp-address.c			\
	camel-object.c				\
	camel-operation.c			\
	camel-partition-table.c			\
	camel-seekable-stream.c			\
	camel-seekable-substream.c		\
	camel-stream-buffer.c			\
	camel-stream-filter.c			\
	camel-stream-fs.c			\
	camel-stream-mem.c			\
	camel-stream-gzip.c			\
	camel-stream-null.c			\
	camel-stream.c				\
	camel-string-utils.c			\
	camel-text-index.c			\
	camel-url-scanner.c			\
	camel-url.c				\
	camel-utf8.c				\
	camel.c					\
	$(LIBCAMEL_PLATFORM_DEP_SOURCES)

if HAVE_CST
libcamel_lite_1_2_la_SOURCES +=	camel-certdb-cst.c
else
libcamel_lite_1_2_la_SOURCES +=	camel-certdb.c
endif


libcamel_liteinclude_HEADERS =			\
	$(providerinclude_headers)		\
	broken-date-parser.h			\
	camel-address.h				\
	camel-arg.h				\
	camel-block-file.h			\
	camel-certdb.h				\
	camel-charset-map.h			\
	camel-data-cache.h			\
	camel-data-wrapper.h			\
	camel-debug.h				\
	camel-exception-list.def		\
	camel-exception.h			\
	camel-file-utils.h			\
	camel-i18n.h				\
	camel-index.h				\
	camel-internet-address.h		\
	camel-junk-plugin.h			\
	camel-list-utils.h			\
	camel-lock-client.h			\
	camel-lock.h				\
	camel-medium.h				\
	camel-mime-filter-basic.h		\
	camel-mime-filter-bestenc.h		\
	camel-mime-filter-canon.h		\
	camel-mime-filter-charset.h		\
	camel-mime-filter-crlf.h		\
	camel-mime-filter-enriched.h		\
	camel-mime-filter-from.h		\
	camel-mime-filter-gzip.h		\
	camel-mime-filter-html.h		\
	camel-mime-filter-index.h		\
	camel-mime-filter-linewrap.h		\
	camel-mime-filter-pgp.h			\
	camel-mime-filter-save.h		\
	camel-mime-filter-tohtml.h		\
	camel-mime-filter-windows.h		\
	camel-mime-filter-yenc.h		\
	camel-mime-filter.h			\
	camel-mime-message.h			\
	camel-mime-parser.h			\
	camel-mime-part-utils.h			\
	camel-mime-part.h			\
	camel-mime-utils.h			\
	camel-multipart-encrypted.h		\
	camel-multipart-signed.h		\
	camel-multipart.h			\
	camel-net-utils.h			\
	camel-nntp-address.h			\
	camel-object.h				\
	camel-operation.h			\
	camel-partition-table.h			\
	camel-search-private.h			\
	camel-seekable-stream.h			\
	camel-seekable-substream.h		\
	camel-stream-buffer.h			\
	camel-stream-filter.h			\
	camel-stream-fs.h			\
	camel-stream-mem.h			\
	camel-stream-gzip.h			\
	camel-stream-null.h			\
	camel-stream-process.h			\
	camel-stream.h				\
	camel-string-utils.h			\
	camel-text-index.h			\
	camel-types.h				\
	camel-url-scanner.h			\
	camel-url.h				\
	camel-utf8.h				\
	camel-lock-helper.h			\
	camel.h

# libcamel_lite_1_2_la_LDFLAGS = -version-info $(LIBCAMEL_CURRENT):$(LIBCAMEL_REVISION):$(LIBCAMEL_AGE) $(NO_UNDEFINED)

libcamel_lite_1_2_la_LIBADD =				\
	$(top_builddir)/libedataserver/libedataserver-${API_VERSION}.la \
	$(top_builddir)/summary/libsummary.la				\
	$(CAMEL_LIBS)							\
	$(SOCKET_LIBS)							\
	$(REGEX_LIBS)							\
	$(SSL_LIBS)                                                     \
	$(top_builddir)/bs/libbodystruct.la 

camel-mime-tables.c: $(srcdir)/gentables.pl
	perl $(srcdir)/gentables.pl > $@

noinst_HEADERS =				\
	broken-date-parser.h			\
	camel-charset-map-private.h		\
	camel-private.h				

EXTRA_DIST =					\
	$(pkgconfig_in_files)	 		\
	gentables.pl

DISTCLEANFILES = $(pkgconfig_DATA)
