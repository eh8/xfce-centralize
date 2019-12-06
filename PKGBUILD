# $Id$
# -------------
# Warning: This package was (poorly) patched to centralize window titles, ignoring any
# other object that a window may or may not have on the left or right side.
# BUGS? Hopefully none :D
# -------------
# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: tobias <tobias funnychar archlinux.org>

pkgname=xfwm4-patch
_pkgname=xfwm4
pkgver=4.12.4
pkgrel=1
pkgdesc="Xfce window manager"
arch=('i686' 'x86_64')
url="http://www.xfce.org/"
license=('GPL2')
groups=('xfce4')
depends=('libxfce4ui' 'libwnck' 'libdrm' 'hicolor-icon-theme')
makedepends=('intltool')
provides=('xfwm4')
conflicts=('xfwm4')
source=(http://archive.xfce.org/src/xfce/$_pkgname/${pkgver%.*}/$_pkgname-$pkgver.tar.bz2
        'centralize.patch')
sha256sums=('fa74048a75649a6e92df763a3cfb706d3fed1e1a6adf567f6693325a5a6efb36'
            'SKIP')

prepare() {
    cd "$srcdir/$_pkgname-$pkgver"
    patch -p0 -i "$srcdir/centralize.patch"
}

build() {
  cd "$srcdir/$_pkgname-$pkgver"

  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib \
    --localstatedir=/var \
    --disable-static \
    --enable-startup-notification \
    --enable-randr \
    --enable-compositor \
    --enable-xsync \
    --disable-debug
  make
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et:
