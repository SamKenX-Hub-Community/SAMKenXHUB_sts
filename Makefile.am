ACLOCAL_AMFLAGS=-I m4

EXTRA_DIST = autogen.sh ChangeLog README.md LICENSE DISCLAIMER

AM_CPPFLAGS = -Wall -Werror
AM_CPPFLAGS += -DOAUTH2_PACKAGE_NAME_VERSION=\"@PACKAGE_NAME@-@PACKAGE_VERSION@\"
AM_CPPFLAGS += $(CODE_COVERAGE_CPPFLAGS) $(CODE_COVERAGE_CFLAGS)
AM_LDFLAGS = --coverage

LDADD = $(CODE_COVERAGE_LIBS)

lib_LTLIBRARIES = @PACKAGE_NAME@.la

@PACKAGE_NAME@_la_CFLAGS = @OAUTH2_CFLAGS@ @OAUTH2_APACHE_CFLAGS@ @APR_CFLAGS@ @XML_CFLAGS@ -Isrc/liboauth2-sts/include
@PACKAGE_NAME@_la_LIBADD = @OAUTH2_LIBS@ @OAUTH2_APACHE_LIBS@ @APR_LIBS@ @XML_LIBS@
@PACKAGE_NAME@_la_SOURCES = \
	src/liboauth2-sts/src/sts.c \
	src/liboauth2-sts/src/wstrust.c \
	src/liboauth2-sts/src/ropc.c \
	src/liboauth2-sts/src/otx.c \
	src/@PACKAGE_NAME@.c	
@PACKAGE_NAME@_la_LDFLAGS = -module

@CODE_COVERAGE_RULES@

clang-format:
	clang-format -style=file -i `find . -name *.[ch]`

install:
	@APXS2@ @APXS2_OPTS@ -i -n @PACKAGE_NAME@ @PACKAGE_NAME@.la