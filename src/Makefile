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

#CFLAGS+= -I${DESTDIR}/usr/include
CFLAGS+= -I${FREEBSD_SRCTOP}/contrib/ofed/include

MAKEFLAGS+= 'CFLAGS+=-I${FREEBSD_SRCTOP}/contrib/ofed/include'
#MAKEFLAGS+= "  -C ${OFED_BINDIR} "

MTREE_FILE=mellanox.bin.dist

#SUBDIRS=${OFED_BINDIR}

SUBTARGETS=clean cleandepend obj depend all install

myall: makestagedirs ${SUBTARGETS}
	echo "******* Building $@"
	#${MAKE} ${MAKEFLAGS} makestagedirs
	#${MAKE} ${MAKEFLAGS} includes
	#${MAKE} ${MAKEFLAGS} depend obj all 

OFED_LIBDIR=${OFED_BINDIR}/usr.lib

my-all-libs: makestagedirs
	env MAKEOBJDIRPREFIX=${DESTDIR} INCLUDEDIR=${DESTDIR}/usr/include && ${MAKE} -C ${OFED_LIBDIR} ${MAKEFLAGS} depend all 
.ifdef STAGEDIR
	-find ${STAGEDIR} -type d -depth -delete -print
.endif

my-install-libs:
	env MAKEOBJDIRPREFIX=${DESTDIR} INCLUDEDIR=${DESTDIR}/usr/include && ${MAKE} -C ${OFED_LIBDIR} ${MAKEFLAGS} install

my-install-includes: makestagedirs
	env MAKEOBJDIRPREFIX=${DESTDIR} INCLUDEDIR=${DESTDIR}/usr/include && ${MAKE} -C ${OFED_BINDIR} ${MAKEFLAGS} includes 
.ifdef STAGEDIR
	-find ${STAGEDIR} -type d -depth -delete -print
.endif

#my-install-includes:
#	env MAKEOBJDIRPREFIX=${DESTDIR} INCLUDEDIR=${DESTDIR}/usr/include && ${MAKE} -C ${OFED_BINDIR} ${MAKEFLAGS} install-includes

none:
	@echo Doing $@


${SUBTARGETS}:  #all clean includes cleandepend obj depend install:
	env MAKEOBJDIRPREFIX=${DESTDIR} INCLUDEDIR=${DESTDIR}/usr/include && ${MAKE} -C ${OFED_BINDIR} ${MAKEFLAGS} $@

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

#.include <bsd.subdir.mk>
