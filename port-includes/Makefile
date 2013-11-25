# New ports collection makefile for:    pstack
# Date created:         1 May 2002
# Whom:                 Peter Edwards <pmedwards@eircom.net>
#
# $FreeBSD: ports/sysutils/pstack/Makefile,v 1.10 2012/11/17 06:01:42 svnexp Exp $
# $Id: Makefile,v 1.2 2002/11/26 10:38:28 pmedwards Exp $
#

PORTNAME=       ofed-includes
PORTVERSION=    1.0
#PORTREVISION=   1

CATEGORIES=     devel

MAINTAINER=     alfred@FreeBSD.org
COMMENT=        includes for ofed

USE_XZ=		yes

FREEBSD_SRCTOP=/usr/src

EXPORT_TAG?=v${PORTVERSION}

EXTRACT_ONLY=
WRKSRC=../src

checksum fetch:
	echo ${.TARGET} not needed because building direct

pre-clean:
	@cd ${WRKSRC} && ${MAKE} clean cleandepend

ALL_TARGET=none

INSTALL_TARGET=my-install-includes

MAKE_JOBS_UNSAFE=yes


.include <bsd.port.mk>

