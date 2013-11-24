# $FreeBSD$

.include <bsd.own.mk>

# Modules that include binary-only blobs of microcode should be selectable by
# MK_SOURCELESS_UCODE option (see below).
#
FREEBSD_SRCTOP?=/usr/src

OFED_BINDIR?=${FREEBSD_SRCTOP}/contrib/ofed

.ifdef STAGEDIR
DESTDIR=${STAGEDIR}
MAKEFLAGS+=	DESTDIR=${STAGEDIR}
.endif

DESTDIR?=/

MTREE_FILE=mellanox.bin.dist

all clean cleandepend obj depend install:
	cd ${OFED_BINDIR} && ${MAKE} ${MAKEFLAGS} $@

makestagedirs:
	mkdir -p ${DESTDIR}
	mtree -deU -f ${MTREE_FILE} -p ${DESTDIR}

#
# mtree -f ../../etc/mtree/BSD.include.dist -p /usr/include -deU
# 

MTREE_ROOT?=/usr/stage
mkmtree:
	mkdir -p \
	    	${MTREE_ROOT}/usr/bin \
	    	${MTREE_ROOT}/usr/lib \
		${MTREE_ROOT}/usr/share/man/man3 \
		${MTREE_ROOT}/usr/include/infiniband/complib \
		${MTREE_ROOT}/usr/include/infiniband/iba \
		${MTREE_ROOT}/usr/include/infiniband/opensm \
		${MTREE_ROOT}/usr/include/infiniband/vendor \
		${MTREE_ROOT}/usr/include/rdma
	mtree -cd -p ${MTREE_ROOT} > ${MTREE_FILE}

.include <bsd.subdir.mk>
