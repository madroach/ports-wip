# $OpenBSD: Makefile,v 1.16 2011/11/01 20:30:49 jasper Exp $

COMMENT =	image manipulation functions for Objective Caml
CATEGORIES =	graphics

V =		4.0.1
DISTNAME =	camlimages-${V}
DISTFILES =	v${V}.tar.gz
MASTER_SITES =	https://bitbucket.org/camlspotter/camlimages/get/
WRKDIST =	${WRKDIR}/camlspotter-camlimages-c803efa9d5d3

MAINTAINER =	Anil Madhavapeddy <avsm@openbsd.org>
HOMEPAGE =	http://cristal.inria.fr/camlimages/

PERMIT_DISTFILES_CDROM =	Yes
PERMIT_DISTFILES_FTP =		Yes
PERMIT_PACKAGE_CDROM =		Yes
PERMIT_PACKAGE_FTP =		Yes

MODULES =	lang/ocaml

WANTLIB +=	c X11 Xpm freetype gif jpeg m png tiff z

LIB_DEPENDS =	graphics/jpeg \
		graphics/libungif \
		graphics/png \
		graphics/tiff
BUILD_DEPENDS =	devel/omake \
		sysutils/findlib \
		print/ghostscript/gnu

# The camlimages build system seems to need some include paths in CPATH and
# others in CFLAGS. I don't know why, but this way at least it works.
MAKE_ENV +=	CPATH="${LOCALBASE}/include/libpng"
MAKE_FLAGS +=	CFLAGS="${CFLAGS} \
			-I${X11BASE}/include \
			-I${X11BASE}/include/X11 \
			-I${LOCALBASE}/include" \
		LDFLAGS=" \
			-L${X11BASE}/lib \
			-L${LOCALBASE}/lib"

# regress exists, but needs manual run and then user interaction
NO_REGRESS =	Yes

OMAKE =		omake --force-dotomake --dotomake ${WRKSRC}/omake_cache

do-build:
	cd ${WRKSRC} && env -i ${MAKE_ENV} ${OMAKE} ${MAKE_FLAGS}

pre-fake:
	${INSTALL_DATA_DIR} ${PREFIX}/lib/ocaml/site-lib
	${INSTALL_DATA_DIR} ${PREFIX}/lib/ocaml/stublibs
	ln -s ../stublibs ${PREFIX}/lib/ocaml/site-lib/

do-install:
	cd ${WRKSRC} && env -i ${MAKE_ENV} \
	${OMAKE} ${ALL_FAKE_FLAGS} ${FAKE_TARGET}

post-install:
	@cp -R ${WRKSRC}/examples/ ${PREFIX}/share/examples/camlimages

.include <bsd.port.mk>
