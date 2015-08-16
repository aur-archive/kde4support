# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kde4support
pkgver=4.98.0
pkgrel=1
pkgdesc='KDE 4 Support'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/frameworks/kde4support'
license=('LGPL')
depends=('kio' 'kunitconversion' 'kdesignerplugin' 'libsm')
makedepends=('extra-cmake-modules' 'kdoctools' 'qt5-tools')
groups=('kf5')
source=("http://download.kde.org/unstable/frameworks/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('d8890517b9fe9b62dcb52c55f857af0a')

prepare() {
  mkdir -p build
}

build() {
  export XDG_DATA_DIRS="/opt/kf5/share:$XDG_DATA_DIRS"

  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
#    -DSYSCONF_INSTALL_DIR=/etc
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
