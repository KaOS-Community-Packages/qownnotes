pkgname=qownnotes
pkgver=16.05.12
pkgrel=1
pkgdesc="Plain-text file notepad and todo list manager with markdown support and ownCloud integration"
arch=('x86_64')
url='https://www.qownnotes.org/'
license=('GPL2')
depends=('qt5-base' 'qt5-svg' 'qt5-declarative' 'openssl')
makedepends=('qt5-tools')
source=("http://downloads.sourceforge.net/project/${pkgname}/src/${pkgname}-${pkgver}.tar.xz")
md5sums=('d60861fa06f6ea2bbe2fc506d901524c')

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

  # make DESTDIR="${pkgdir}/" install

  # install application
  install -D -m755 QOwnNotes "${pkgdir}/usr/bin/QOwnNotes"

  # install visuals
  install -D -m644 QOwnNotes.desktop "${pkgdir}/usr/share/applications/QOwnNotes.desktop"
  install -D -m644 "images/icons/128x128/QOwnNotes.png" "${pkgdir}/usr/share/pixmaps/QOwnNotes.png"
  for format in {16x16,24x24,32x32,48x48,64x64,96x96,128x128,256x256,512x512}; do
    install -D -m644 "images/icons/${format}/QOwnNotes.png" "${pkgdir}/usr/share/icons/hicolor/$format/apps/QOwnNotes.png"
  done
  install -D -m644 "images/icons/scalable/QOwnNotes.svg" "${pkgdir}/usr/share/icons/hicolor/scalable/apps/QOwnNotes.svg"

  # install languages
  install -d "${pkgdir}/usr/share/QOwnNotes/languages/"
  install -D -m644 languages/*.qm "${pkgdir}/usr/share/QOwnNotes/languages/"
}
