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

#VALID_CATEGORIES+= zfs
#CATEGORIES+=     zfs

MAINTAINER=     alfred@FreeBSD.org
COMMENT=        libraries for ofed


#NO_STAGE=yes
USE_XZ=		yes

FREEBSD_SRCTOP=/usr/src


EXPORT_TAG?=v${PORTVERSION}
#GIT_ZFS_REPO?=github.com:/freebsd/freebsd

# Make a tarball from git for ourselves.
git-export:
	git archive \
		--remote=${GIT_ZFS_REPO} \
		--prefix=${PORTNAME}-${PORTVERSION}/ \
		${EXPORT_TAG} | \
			xz > ${PORTNAME}-${PORTVERSION}.tar.xz

NAS_PORTS_DIRECT=YES

# if NAS_PORTS_DIRECT or NAS_PORTS_DIRECT_SYSUTILS_ZFSD is set
# then what we do is use the checked out copy of ZFSD.
.if defined(NAS_PORTS_DIRECT) ||defined(NAS_PORTS_DIRECT_MISC_TRUENAS_FILES)

EXTRACT_ONLY=
WRKSRC=../src
#WRKSRC=/home/alfred/tn/zfsd

# no checksum, we just used git!
 #extract:
checksum fetch:
	echo ${.TARGET} not needed because building direct

pre-clean:
	@cd ${WRKSRC} && ${MAKE} clean cleandepend

ALL_TARGET=depend obj all

MAKE_JOBS_UNSAFE=yes

.endif

#
# Uncomment to test using git to pull sources instead of tarball
# EXTRACT_DEPENDS= ${LOCALBASE}/bin/git:${PORTSDIR}/devel/git
#extract:
#		mkdir -p ${WRKDIR}
#		git clone -b /truenas-build/git-repo/zfsd.git ${WRKSRC}


.include <bsd.port.mk>

