# Maintainer: Rustmilian <######[@]######[.]me>

pkgname=kdbusaddons-git
pkgver=5.240.0_r467.g455e1e3
pkgrel=1
pkgdesc='Addons to QtDBus'
arch=($CARCH)
url='https://invent.kde.org/frameworks/kdbusaddons'
license=(LGPL)
depends=()
makedepends=(git extra-cmake-modules-git qt6-tools clang python-pyqt6 doxygen sip4)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('python-pyqt6: for the Python bindings')
groups=(kf6-git)
source=("git+${url}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DQT_MAJOR_VERSION=6 \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
