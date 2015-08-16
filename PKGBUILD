pkgname=kvirc4-svn-light
pkgver=6381
pkgrel=1
pkgdesc="Qt4 based IRC-Client - SVN version with light compilation"
arch=('i686' 'x86_64')
url="http://www.kvirc.net"
license=('GPL')
depends=('qt4' 'glibc' 'openssl' 'zlib')
makedepends=('cmake' 'subversion' 'automoc4' 'gettext')
conflicts=('kvirc4' 'kvirc')
provides=('kvirc' 'kvirc4')
source=("svn+https://svn.kvirc.de/svn/trunk/kvirc")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/kvirc"
  svnversion | tr -d [A-z]
}

build() {
  cd "$srcdir/kvirc"
  cmake -DWANT_QTDBUS=OFF \
        -DWANT_KDE4=OFF \
        -DWANT_QT4=ON \
        -DWANT_PHONON=OFF \
        -DWANT_QTWEBKIT=OFF \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DWANT_COEXISTENCE=OFF \
        -DWANT_AUDIOFILE=OFF \
        -DWANT_TRANSPARENCY=OFF \
        -DWANT_PERL=OFF \
        -DWANT_PYTHON=OFF \
        -DWANT_IPC=OFF \
        -DWANT_GSM=OFF \
        -DWANT_DCC_VOICE=OFF \
        -DWANT_DOXYGEN=OFF \
        -DWANT_CRYPT=OFF
  make
}

package() {
  cd "$srcdir/kvirc"
  make DESTDIR="$pkgdir" install
}
