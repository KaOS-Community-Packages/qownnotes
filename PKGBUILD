pkgname=qownnotes
pkgver=16.06.13
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('qt5-base' 'qt5-svg' 'qt5-declarative' 'openssl')
rodepends=('hicolor-icon-theme') ## no need for /pixmaps/ so I think
makedepends=('qt5-tools')
source=(http://downloads.sourceforge.net/project/${pkgname}/src/${pkgname}-${pkgver}.tar.xz \
            add-install-targets.patch)
md5sums=('94de74903397094d4982a05418743a31' '410c56b9388289fd09e69173d98e00c1')

prepare() {
  cd "${pkgname}-${pkgver}"
  ## wth manually install these days :-) -- crazy --
  patch -Np1 <../add-install-targets.patch
  
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
