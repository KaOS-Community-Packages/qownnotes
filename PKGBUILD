pkgname=qownnotes
pkgver=19.11.9
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('sonnet' 'qt5-base' 'qt5-tools' 'qt5-declarative' 'qt5-svg' 'qt5-websockets' 'qt5-xmlpatterns' 'openssl')
makedepends=('qt5-tools')
source=("https://download.tuxfamily.org/${pkgname}/src/${pkgname}-${pkgver}.tar.xz")
sha256sums=('c7883965e9ee7878321a36c132c4dc9b2b34569c50b91a1e7466ee5e50fa1b84')

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
