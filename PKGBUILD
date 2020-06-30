# $Id$
# Maintainer: Julio Arias <jarias01@gmail.com>

pkgname=slstatus
pkgver=r552.b14e039
pkgrel=1
pkgdesc='A status monitor for window managers'
arch=('i686' 'x86_64')
url='http://tools.suckless.org/slstatus'
depends=('libx11')
makedepends=('git')
license=('custom:ISC')
source=("git+https://git.suckless.org/${pkgname%-git}"
        "config.h")
sha256sums=('SKIP'
         '4c02a315b73c9947c9fb6afcc36971b24fd58bf76914de73c69444bebd72f381')

pkgver() {
    cd "${pkgname%-git}"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
    cp config.h "${pkgname%-git}/config.h"
}

build() {
    cd "${pkgname%-git}"
    make X11INC='/usr/include/X11' X11LIB='/usr/lib/X11'
}

package() {
    cd "${pkgname%-git}"
    make DESTDIR="${pkgdir}" install
}
