# $NetBSD: Makefile,v 1.4 2018/05/12 01:25:23 markd Exp $

DISTNAME=	polyglossia
PKGNAME=	tex-${DISTNAME}-1.43
TEXLIVE_REV=	47392

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://ctan.org/pkg/polyglossia
COMMENT=	An alternative to babel for XeLaTeX and LuaLaTeX
LICENSE=	lppl-1.3c

DEPENDS+=	tex-etoolbox>=2.1d:../../devel/tex-etoolbox
DEPENDS+=	tex-fontspec>=2.4c:../../fonts/tex-fontspec
DEPENDS+=	tex-makecmds-[0-9]*:../../print/tex-makecmds
DEPENDS+=	xetex>=0.9995.3nb1:../../print/xetex

.include "../../print/texlive/package.mk"
.include "../../mk/bsd.pkg.mk"
