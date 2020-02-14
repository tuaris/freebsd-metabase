# $FreeBSD: $

PORTNAME=	metabase
PORTVERSION=	0.34.2
DISTVERSIONPREFIX=	v
CATEGORIES=	databases
MASTER_SITES=	https://downloads.metabase.com/${DISTVERSIONPREFIX}${PORTVERSION}/

MAINTAINER=	daniel@morante.net
COMMENT=	Simple and powerful analytics tool that supports multiple data stores

LICENSE=	AGPLv3

DIST_SUBDIR=	${PORTNAME}-${PORTVERSION}
DISTFILES=	${PORTNAME}.jar
EXTRACT_ONLY=

USERS=          ${PORTNAME}
GROUPS=         ${PORTNAME}

USE_RC_SUBR=	${PORTNAME}
SUB_LIST+=	PORTNAME=${PORTNAME} \
			METABASEDATADIR=/var/db/${PORTNAME} \
			METABASE_USER=${PORTNAME} \
			METABASE_GROUP=${PORTNAME} \
			JAVA_HOME=${JAVA_HOME}

SUB_FILES=      pkg-message

USE_JAVA=	yes
NO_BUILD=	yes
NO_ARCH=	yes
JAVA_RUN=	yes

PLIST_FILES?=   bin/${PORTNAME}.jar "@sample etc/${PORTNAME}.conf.sample"

do-install:
	${INSTALL_DATA} ${DISTDIR}/${DIST_SUBDIR}/${PORTNAME}.jar \
		${STAGEDIR}${PREFIX}/bin/${PORTNAME}.jar
	${INSTALL_DATA} ${FILESDIR}/${PORTNAME}.conf \
		${STAGEDIR}${PREFIX}/etc/${PORTNAME}.conf.sample

.include <bsd.port.mk>
