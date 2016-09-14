pkgname=qownnotes
pkgver=16.09.6
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('qt5-base' 'qt5-svg' 'qt5-declarative' 'openssl')
makedepends=('qt5-tools')
source=("http://downloads.sourceforge.net/project/${pkgname}/src/${pkgname}-${pkgver}.tar.xz")
md5sums=('c4d53c0bc797ae2dd67ca44ad89a56dc')

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
