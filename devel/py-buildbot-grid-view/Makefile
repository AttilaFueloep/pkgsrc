# $NetBSD: Makefile,v 1.5 2018/08/28 07:26:19 adam Exp $

DISTNAME=	buildbot-grid-view-1.3.0
PKGNAME=	${PYPKGPREFIX}-${DISTNAME}
CATEGORIES=	devel net python
MASTER_SITES=	${MASTER_SITE_PYPI:=b/buildbot-grid-view/}

MAINTAINER=	joerg@NetBSD.org
HOMEPAGE=	https://buildbot.net/
COMMENT=	Grid View Plugin for the buildbot CI system
LICENSE=	gnu-gpl-v2

DEPENDS+=	${PYPKGPREFIX}-buildbot-[0-9]*:../../devel/py-buildbot
BUILD_DEPENDS+=	${PYPKGPREFIX}-buildbot-pkg-[0-9]*:../../devel/py-buildbot-pkg

USE_LANGUAGES=	# none

.include "../../lang/python/egg.mk"
.include "../../mk/bsd.pkg.mk"
