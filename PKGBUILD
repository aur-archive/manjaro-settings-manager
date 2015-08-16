# Maintainer: Philip Müller <philm[at]manjaro[dog]org>
# Maintainer: Roland Singer <roland[at]manjaro[dog]org>

pkgname=manjaro-settings-manager
pkgver=0.4.9
pkgrel=2
pkgdesc="Manjaro Linux System Settings Tool"
arch=('i686' 'x86_64')
url="http://git.manjaro.org"
license=('GPL')
depends=('ckbcomp' 'qt5-webkit' 'icu' 'hwinfo' 'kitemmodels')
makedepends=('qt5-tools')
optdepends=('kdesu: for KDE'
            'gksu: for XFCE, Gnome, LXDE, Cinnamon'
            'gnome-keyring: for password management'
            'polkit: as an alternative su tool')
replaces=('manjaro-system-settings')
provides=('manjaro-system-settings')
conflicts=('manjaro-system-settings')
install=$pkgname.install
source=("https://github.com/manjaro/$pkgname/archive/$pkgver.tar.gz")
sha256sums=('6c3d7b2cfa0e2e92e7b80d81e59f5d8e59d25e864f9ac5ac3ffdb03e0101c5f0')

build() {
  cd "$srcdir/$pkgname-$pkgver/src"

  /usr/lib/qt/bin/lrelease $pkgname/$pkgname.pro
  /usr/lib/qt/bin/lrelease $pkgname-daemon/$pkgname-daemon.pro

  qmake-qt5

  # Build fix
  make sub-global-all
  cp global/libglobal.a libglobal.a

  make all
}

package() {
  cd "$srcdir/$pkgname-$pkgver/src"
  make INSTALL_ROOT="${pkgdir}" install
}
