pkgname=qownnotes
pkgver=19.11.2
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('sonnet' 'qt5-base' 'qt5-tools' 'qt5-declarative' 'qt5-svg' 'qt5-websockets' 'qt5-xmlpatterns' 'openssl')
makedepends=('qt5-tools')
source=("https://download.tuxfamily.org/${pkgname}/src/${pkgname}-${pkgver}.tar.xz")
sha256sums=('ea77511ee9067d1e8e3eb6e7dfcc0705200fde5bd945093fb11600db4437e875')

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
