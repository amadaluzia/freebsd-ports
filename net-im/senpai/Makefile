PORTNAME=	senpai
DISTVERSIONPREFIX=	v
DISTVERSION=	0.5.0
CATEGORIES=	net-im

MAINTAINER=	amadaluzia@disroot.org
COMMENT=	Modern terminal IRC client
WWW=		https://sr.ht/~delthas/senpai

LICENSE=	ISCL
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	scdoc:textproc/scdoc

USES=		desktop-file-utils gmake go:modules
GO_MODULE=	git.sr.ht/~delthas/senpai
GO_TARGET=	./cmd/senpai
GO_LDFLAGS=	-X git.sr.ht/~delthas/senpai.version=${DISTVERSIONFULL}

post-build:
	${MAKE_CMD} -C ${WRKSRC} ${MAKE_ARGS} doc
	${MAKE_CMD} -C ${WRKSRC} ${MAKE_ARGS} res

post-install:
	${INSTALL_MAN} ${WRKSRC}/doc/senpai.1 ${STAGEDIR}${PREFIX}/share/man/man1
	${INSTALL_MAN} ${WRKSRC}/doc/senpai.5 ${STAGEDIR}${PREFIX}/share/man/man5
	${MKDIR} ${STAGEDIR}${PREFIX}/share/applications
	${INSTALL_DATA} ${WRKSRC}/contrib/senpai.desktop ${STAGEDIR}${PREFIX}/share/applications/senpai.desktop
	${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/scalable/apps
	${INSTALL_DATA} ${WRKSRC}/res/icon.svg ${STAGEDIR}${PREFIX}/share/icons/hicolor/scalable/apps/senpai.svg
	${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/48x48/apps
	${INSTALL_DATA} ${WRKSRC}/res/icon.48.png ${STAGEDIR}${PREFIX}/share/icons/hicolor/48x48/apps/senpai.png

.include <bsd.port.mk>
