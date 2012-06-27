# $OpenBSD:$
COMMENT =		network protocol analyzer
VERSION =		1.6.0
DISTNAME =		wireshark-${VERSION}

SHARED_LIBS +=		wireshark 0.23
SHARED_LIBS +=		wiretap 0.23
SHARED_LIBS +=		wsutil 0.23

CATEGORIES =		net
MAINTAINER =		Nigel Taylor <njtaylor@asterisk.demon.co.uk>

HOMEPAGE =		http://www.wireshark.org/

# GPLv2
PERMIT_PACKAGE_CDROM =	 Yes
PERMIT_PACKAGE_FTP =	 Yes
PERMIT_DISTFILES_CDROM = Yes
PERMIT_DISTFILES_FTP =	 Yes

EXTRACT_SUFX =		.tar.bz2
MASTER_SITES =		http://www.wireshark.org/download/src/ \
			${MASTER_SITE_SOURCEFORGE:=wireshark/}

WANTLIB += 		c z m pango-1.0 pthread pcap \
			gdk-x11-2.0 gdk_pixbuf-2.0 gtk-x11-2.0 \
			glib-2.0 gmodule-2.0 gobject-2.0  gthread-2.0 \
			lua gpg-error adns gnutls portaudio gcrypt

MODULES = 		lang/python

BUILD_DEPENDS =		x11/gtk+2 \
			devel/atk \
			graphics/tiff \
			devel/glib2 \
			graphics/jpeg

RUN_DEPENDS =		${BUILD_DEPENDS}

LIB_DEPENDS =		lang/lua \
			security/libgpg-error \
			net/adns \
			security/gnutls \
			audio/portaudio-svn \
			security/libgcrypt

USE_GMAKE =		Yes
USE_LIBTOOL =		Yes
USE_GROFF =		Yes

CONFIGURE_STYLE =	gnu	
CONFIGURE_ARGS +=	${CONFIGURE_SHARED} \
			--with-ssl \
			--enable-threads

NO_REGRESS =		Yes

.include <bsd.port.mk>
