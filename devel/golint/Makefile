# $NetBSD: Makefile,v 1.13 2018/10/10 19:16:26 bsiegert Exp $

DISTNAME=		golint-20180702
CATEGORIES=		devel
MASTER_SITES=		${MASTER_SITE_GITHUB:=golang/}
GITHUB_PROJECT=		lint
GITHUB_TAG=		06c8688

MAINTAINER=		bsiegert@NetBSD.org
HOMEPAGE=		https://golang.org/
COMMENT=		Linter for Go source files
LICENSE=		modified-bsd

GO_SRCPATH=		golang.org/x/lint
GO_DIST_BASE=		${GITHUB_PROJECT}-${GITHUB_TAG}*

CHECK_RELRO_SKIP+=	bin/golint

do-install:
	${INSTALL_PROGRAM} ${WRKDIR}/bin/golint ${DESTDIR}${PREFIX}/bin


.include "../../lang/go/go-package.mk"
.include "../../devel/go-tools/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
