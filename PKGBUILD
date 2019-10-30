pkgname=qownnotes
pkgver=19.10.13
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('sonnet' 'qt5-base' 'qt5-tools' 'qt5-declarative' 'qt5-svg' 'qt5-websockets' 'qt5-xmlpatterns' 'openssl')
makedepends=('qt5-tools')
source=("https://download.tuxfamily.org/${pkgname}/src/${pkgname}-${pkgver}.tar.xz")
sha256sums=('5ec3ca42fb5836882604a3750a1d9540a56dfcc0390f5fecd8fecfe39f0cd1cd')

prepare() {
  cd "${pkgname}-${pkgver}"

  # set KCP as origin
  echo "#define RELEASE \"KCP\"" > release.h

  # enforce spellchecking with Sonnet
  sed -i 's|#CONFIG += with_sonnet|CONFIG += with_sonnet|' QOwnNotes.pro
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
