# $NetBSD: Makefile,v 1.9 2018/07/03 05:03:21 adam Exp $

DISTNAME=	xdot
PKGNAME=	xdot-20121124
CATEGORIES=	graphics
#MASTER_SITES=	http://xdot.jrfonseca.googlecode.com/git/
EXTRACT_SUFX=	.py

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	https://github.com/jrfonseca/xdot.py
COMMENT=	Interactive viewer for graphs written in Graphviz's dot language
LICENSE=	gnu-lgpl-v3

DEPENDS+=	${PYPKGPREFIX}-gtk2-[0-9]*:../../x11/py-gtk2

WRKSRC=		${WRKDIR}
USE_LANGUAGES=	# none
DIST_SUBDIR=	${PKGNAME_NOREV}
REPLACE_PYTHON=	xdot.py
PYTHON_VERSIONS_INCOMPATIBLE=	34 35 36 37 # py-gtk2
INSTALLATION_DIRS=	bin

do-build:

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/xdot.py ${DESTDIR}${PREFIX}/bin/xdot

.include "../../lang/python/application.mk"
.include "../../mk/bsd.pkg.mk"
