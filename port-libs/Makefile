# New ports collection makefile for:    pstack
# Date created:         1 May 2002
# Whom:                 Peter Edwards <pmedwards@eircom.net>
#
# $FreeBSD: ports/sysutils/pstack/Makefile,v 1.10 2012/11/17 06:01:42 svnexp Exp $
# $Id: Makefile,v 1.2 2002/11/26 10:38:28 pmedwards Exp $
#

PORTNAME=       ofed-libs
PORTVERSION=    1.0
#PORTREVISION=   1

CATEGORIES=     devel

# busted for non-ports ports
#BUILD_DEPENDS=	ofed-includes:../port-includes

MAINTAINER=     alfred@FreeBSD.org
COMMENT=        libraries for ofed

USE_XZ=		yes

FREEBSD_SRCTOP=/usr/src

EXPORT_TAG?=v${PORTVERSION}

EXTRACT_ONLY=
WRKSRC=../src

checksum fetch:
	echo ${.TARGET} not needed because building direct

pre-clean:
	@cd ${WRKSRC} && ${MAKE} clean cleandepend

ALL_TARGET=my-all-libs

INSTALL_TARGET=my-install-libs
# makestagedirs includes depend obj all

MAKE_JOBS_UNSAFE=yes


.include <bsd.port.mk>

