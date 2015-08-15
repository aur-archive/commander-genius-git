# Maintainer: Peter Lewis <plewis@aur.archlinux.org>
pkgname=commander-genius-git
_pkgname=Commander-Genius
pkgver=v161release.r199.gbaebe2c
pkgrel=1
pkgdesc="A modern implementation of the classic game Commander Keen"
arch=('i686' 'x86_64')
url="http://clonekeenplus.sourceforge.net"
license=('GPL')
groups=()
depends=('sdl' 'mesa' 'libvorbis' 'sdl_image' 'boost')
makedepends=('git' 'cmake' 'glu')
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
source=(git+https://github.com/gerstrong/Commander-Genius.git)
noextract=()
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  echo $(git describe --long --tags | sed -r 's/([^-]*-g)/r\1/;s/-/./g')
}


build() {
  cd "$srcdir/$_pkgname"
  sed -i 's/APPDIR\ games/APPDIR\ bin/' install.cmake

  [ $CARCH == 'x86_64' ] && cmake -DBUILD_TYPE=LINUX64 -DCMAKE_INSTALL_PREFIX=/usr
  [ $CARCH == 'i686' ] && cmake -DBUILD_TYPE=LINUX32 -DCMAKE_INSTALL_PREFIX=/usr

  make
}

package() {
  cd "$srcdir/$_pkgname"
  make DESTDIR="$pkgdir/" install
}
