# $FreeBSD$

.include <bsd.own.mk>

# Modules that include binary-only blobs of microcode should be selectable by
# MK_SOURCELESS_UCODE option (see below).
#
FBSD_SRCTOP?=/usr/src

OFED_LIBDIR?=${FBSD_SRCTOP}/contrib/ofed/usr.lib

.ifdef STAGEDIR
DESTDIR=${STAGEDIR}
MAKEFLAGS+=	DESTDIR=${STAGEDIR}
.endif

DESTDIR?=/

MTREE_FILE=mellanox.lib.dist

all clean cleandepend obj depend install:
.ifmake install
	mtree -deU -f ${MTREE_FILE} -p ${DESTDIR}
.endif
	cd ${OFED_LIBDIR} && ${MAKE} ${MAKEFLAGS} $@


MTREE_ROOT?=/usr/stage
mkmtree:
	mkdir -p \
	    	${MTREE_ROOT}/usr/lib \
		${MTREE_ROOT}/usr/share/man/man3
	mtree -cd -p ${MTREE_ROOT} > ${MTREE_FILE}

.include <bsd.subdir.mk>
