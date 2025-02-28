PORTNAME=	certctl
DISTVERSION=	g20250227
CATEGORIES=	local security
MASTER_SITES=	GH

MAINTAINER=	rincorvid@gmail.com
COMMENT=	Modified certctl(8) with CAfile support

LICENSE=	BSD2CLAUSE

USE_GITHUB=	yes
GH_ACCOUNT=	rincorvid
GH_TAGNAME=	01a43e6

NO_ARCH=	yes
NO_BUILD=	yes

.include <bsd.port.pre.mk>

_BINDIR=	sbin
_MANDIR=	share/man/man8
MANDIRS+=	/usr/${_MANDIR}

do-install:
.for i in /usr ${PREFIX}
	${MKDIR} ${STAGEDIR}${i}/${_BINDIR} ${STAGEDIR}${i}/${_MANDIR}
	${INSTALL_SCRIPT} ${WRKSRC}/certctl.sh ${STAGEDIR}${i}/${_BINDIR}/certctl
	${INSTALL_MAN}    ${WRKSRC}/certctl.8  ${STAGEDIR}${i}/${_MANDIR}/certctl.8
.endfor

.include <bsd.port.post.mk>
