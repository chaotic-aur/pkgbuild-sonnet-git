# Merged with official ABS sonnet PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: zan <zan@420blaze.it>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Stefan Husmann <stefan-husmann@t-online.de>

pkgname=sonnet-git
pkgver=5.80.0_r592.gd6d4e94
pkgrel=1
pkgdesc='Spelling framework for Qt5'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(qt5-base)
makedepends=(git extra-cmake-modules-git qt5-tools qt5-doc hunspell aspell hspell libvoikko doxygen qt5-quickcontrols)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('hunspell: spell checking via hunspell' 'aspell: spell checking via aspell'
            'hspell: spell checking for Hebrew' 'libvoikko: Finnish support via Voikko')
groups=(kf5-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
source=("git+https://github.com/KDE/${pkgname%-git}#branch=kf5")
