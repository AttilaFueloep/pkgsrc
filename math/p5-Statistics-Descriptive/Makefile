# $NetBSD: Makefile,v 1.19 2018/08/22 09:45:41 wiz Exp $

DISTNAME=	Statistics-Descriptive-3.0701
PKGNAME=	p5-${DISTNAME}
PKGREVISION=	1
CATEGORIES=	math perl5
MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=Statistics/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://search.cpan.org/dist/Statistics-Descriptive/
COMMENT=	Perl module of basic descriptive statistical functions
LICENSE=	${PERL5_LICENSE}

PERL5_PACKLIST=		auto/Statistics/Descriptive/.packlist
PERL5_MODULE_TYPE=	Module::Build

DEPENDS+=	p5-List-MoreUtils>=0:../../devel/p5-List-MoreUtils

.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
