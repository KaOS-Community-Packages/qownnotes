pkgname=qownnotes
pkgver=19.11.8
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('sonnet' 'qt5-base' 'qt5-tools' 'qt5-declarative' 'qt5-svg' 'qt5-websockets' 'qt5-xmlpatterns' 'openssl')
makedepends=('qt5-tools')
source=("https://download.tuxfamily.org/${pkgname}/src/${pkgname}-${pkgver}.tar.xz")
sha256sums=('026e6606fff46df3696af4f74d9f93930495ae7fc7d69c158a3470b81b4cfe37')

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
