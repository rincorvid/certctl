PORTNAME=	ca_root_nss
PORTVERSION=	${VERSION_NSS}
PORTREVISION=	1
CATEGORIES=	security
MASTER_SITES=	MOZILLA/security/nss/releases/${DISTNAME:tu:C/[-.]/_/g}_RTM/src
DISTNAME=	nss-${VERSION_NSS}${NSS_SUFFIX}

MAINTAINER=	ports-secteam@FreeBSD.org
COMMENT=	Root certificate bundle from the Mozilla Project

LICENSE=	MPL20
LICENSE_FILE=	${WRKSRC}/COPYING

USES=		perl5 ssl:build
USE_PERL5=	build

NO_ARCH=	yes
WRKSRC_SUBDIR=	nss

OPTIONS_DEFINE=		KEEPCAFILE
OPTIONS_DEFAULT=	KEEPCAFILE

OPTIONS_SUB=		yes

KEEPCAFILE_DESC=	Update, not delete, CAfiles on uninstall

CERTDIR?=	share/certs
PLIST_SUB+=	CERTDIR=${CERTDIR}

VERSION_NSS=	3.108
CERTDATA_TXT_PATH=	lib/ckfw/builtins/certdata.txt
BUNDLE_PROCESSOR=	MAca-bundle.pl

SUB_FILES=	MAca-bundle.pl
SUB_LIST=	VERSION_NSS=${VERSION_NSS}

do-build:
	@${SETENV} PATH=${LOCALBASE}/bin:$${PATH} \
		${PERL} ${WRKDIR}/${BUNDLE_PROCESSOR} \
	    < ${WRKSRC}/${CERTDATA_TXT_PATH} > \
	    ${WRKDIR}/ca-root-nss.crt

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${CERTDIR}
	${INSTALL_DATA} ${WRKDIR}/ca-root-nss.crt ${STAGEDIR}${PREFIX}/${CERTDIR}

.include <bsd.port.mk>
