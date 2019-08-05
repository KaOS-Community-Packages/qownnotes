pkgname=qownnotes
pkgver=19.8.2
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('qt5-base' 'qt5-declarative' 'qt5-svg' 'qt5-websockets' 'qt5-xmlpatterns' 'openssl')
makedepends=('qt5-tools')
source=("https://download.tuxfamily.org/${pkgname}/src/${pkgname}-${pkgver}.tar.xz")
sha256sums=('60f3f83cf41d62e1b873435fc7ed77d7c9cd37e6e5f7dfc69d4e3c6ff351e2e2')

prepare() {
  cd "${pkgname}-${pkgver}"

  echo "#define RELEASE \"KCP\"" > release.h
}

build() {
  cd "${pkgname}-${pkgver}"

  qmake-qt5
  make
}

package() {
  cd "${pkgname}-${pkgver}"

  make INSTALL_ROOT="${pkgdir}/" install
}
