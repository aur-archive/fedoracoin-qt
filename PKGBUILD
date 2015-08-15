# fedoracoin-qt Arch PKGBUILD
# Maintainer mxtm <max@mxtm.me>
# Based off of the dogecoin-qt-git PKGBUILD, based off of primecoin-qt's PKGBUILD by Daniel Spies

pkgname=fedoracoin-qt
_binname=fedoracoin
pkgver=1.0
pkgrel=1
pkgdesc="A QT wallet for the FedoraCoin cryptocurrency."
arch=('x86_64' 'i686')
url="http://fedoraco.in"
license=('MIT')
provides=('fedoracoin-qt')
depends=('qt4' 'miniupnpc' 'boost-libs')
makedepends=('boost' 'gcc' 'make' 'git')
source=('http://files.fedoraco.in/'${pkgver}'/fedoracoin-'${pkgver}'.tar.gz'
        'fedoracoin.desktop')
install=fedoracoin-qt.install

sha256sums=('5e02afdc5a691cedd97a367224936cdbc029ddbc326841a30868c2a5923f58fb'
            'c452d62cfae7c5a5fbb6ce82a50dc844816e9c0517f8216d8ba393cfaf86b88f')

# files & commands for building
_qmake=qmake-qt4

build() {
	tar -xvzf ${_binname}-${pkgver}.tar.gz

	cd ${_binname}-${pkgver}

	${_qmake} ${_binname}-qt.pro
		
	make ${MAKEFLAGS} || make ${MAKEFLAGS}
}

package() {
	install -Dm644 ${_binname}.desktop ${pkgdir}/usr/share/applications/${_binname}.desktop

	cd ${_binname}-${pkgver}
	install -Dm755 ${_binname}-qt "$pkgdir"/usr/bin/${_binname}-qt
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
	install -Dm644 src/qt/res/icons/bitcoin.png "$pkgdir"/usr/share/pixmaps/${_binname}.png
}
