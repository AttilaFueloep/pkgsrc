# $NetBSD: Makefile,v 1.48 2018/09/10 09:07:49 schmonz Exp $
#

DISTNAME=		qmail-run-20180910
CATEGORIES=		mail
MASTER_SITES=		# empty
DISTFILES=		# empty

MAINTAINER=		schmonz@NetBSD.org
COMMENT=		Configures qmail to receive and deliver mail
LICENSE=		2-clause-bsd

DEPENDS+=		mess822-[0-9]*:../../mail/mess822
DEPENDS+=		pkg_alternatives-[0-9]*:../../pkgtools/pkg_alternatives
DEPENDS_QMAIL=		qmail>=1.03nb36:../../mail/qmail
DEPENDS+=		${DEPENDS_QMAIL}
DEPENDS+=		qmail-qfilter>1.5nb1:../../mail/qmail-qfilter
DEPENDS+=		qmail-rejectutils-[0-9]*:../../mail/qmail-rejectutils

WRKSRC=			${WRKDIR}
NO_BUILD=		yes
NO_CHECKSUM=		yes

FILES_SUBST+=		QMAIL_DAEMON_USER=${QMAIL_DAEMON_USER:Q}
FILES_SUBST+=		QMAIL_LOG_USER=${QMAIL_LOG_USER:Q}
FILES_SUBST+=		QMAIL_SEND_USER=${QMAIL_SEND_USER:Q}
FILES_SUBST+=		QMAIL_QUEUE_EXTRA=${QMAIL_QUEUE_EXTRA:Q}
FILES_SUBST+=		PKGNAME=${PKGNAME:Q}
MESSAGE_SUBST+=		PKG_SYSCONFBASE=${PKG_SYSCONFBASE:Q}
RCD_SCRIPTS=		qmail qmailofmipd qmailpop3d qmailqread qmailsend qmailsmtpd

INSTALLATION_DIRS=	bin share/doc/qmail-run share/examples/qmail-run
BUILD_DEFS+=		QMAIL_DAEMON_USER QMAIL_LOG_USER QMAIL_SEND_USER
BUILD_DEFS+=		QMAIL_QUEUE_EXTRA PKG_SYSCONFBASE

.include "../../mk/bsd.prefs.mk"

# Detect the PKG_SYSCONFDIR of the installed qmail, so we can create
# config files there and refer to them from rc.d scripts.
#
.if !defined(PKG_SYSCONFDIR.qmail-run)
PKG_SYSCONFDIR.qmail-run!=						\
	${PKG_INFO} -Q PKG_SYSCONFDIR					\
		${DEPENDS_QMAIL:C/:.*$//:Q} 2>/dev/null ||		\
	${ECHO} "PKG_SYSCONFDIR.qmail-run_not_set"
.  if empty(PKG_SYSCONFDIR.qmail-run:M*not_set)
MAKEVARS+=	PKG_SYSCONFDIR.qmail-run
.  endif
.endif

SUBST_CLASSES+=		paths
SUBST_STAGE.paths=	pre-configure
SUBST_FILES.paths=	mailer.conf qmail-isspam-* qmail-procmail
SUBST_FILES.paths+=	qmail-qread-client spamdyke-ofmipd.conf
SUBST_VARS.paths=	PKGNAME PKG_SYSCONFDIR PREFIX
SUBST_VARS.paths+=	CAT ECHO GREP SED SH SORT TRUE

.include "options.mk"

post-extract:
	for f in README.pkgsrc mailer.conf spamdyke-ofmipd.conf stunnel.conf; do \
	    ${CP} ${FILESDIR}/$$f ${WRKDIR}/$$f;			\
	done
	for f in qmail-isspam-rspamd qmail-isspam-spamassassin \
		qmail-procmail qmail-qread-client; do \
	    ${CP} ${FILESDIR}/$$f.sh ${WRKDIR}/$$f;			\
	done

do-install:
	for f in qmail-isspam-rspamd qmail-isspam-spamassassin \
		qmail-procmail qmail-qread-client; do \
	    ${INSTALL_SCRIPT} ${WRKDIR}/$$f ${DESTDIR}${PREFIX}/bin;	\
	done
	${INSTALL_DATA} ${WRKDIR}/README.pkgsrc \
		${DESTDIR}${PREFIX}/share/doc/qmail-run
	${INSTALL_DATA} ${WRKDIR}/mailer.conf \
		${DESTDIR}${PREFIX}/share/examples/qmail-run
	${INSTALL_DATA} ${WRKDIR}/spamdyke-ofmipd.conf \
		${DESTDIR}${PREFIX}/share/examples/qmail-run
	${INSTALL_DATA} ${WRKDIR}/stunnel.conf \
		${DESTDIR}${PREFIX}/share/examples/qmail-run

.include "../../mk/bsd.pkg.mk"
