# Maintainer: SpepS <dreamspepser at yahoo dot it>

pkgname=serd
pkgver=0.14.0
pkgrel=1
pkgdesc="A lightweight C library for RDF syntax which supports reading and writing Turtle and NTriples."
arch=(i686 x86_64)
url="http://drobilla.net/software/$pkgname/"
license=('custom:ISC')
depends=('glibc')
makedepends=('python2')
source=("http://download.drobilla.net/$pkgname-$pkgver.tar.bz2")
md5sums=('405b11ee92f3f19ce4a757ba34953886')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # remove ldconfig
  sed -i "/ldconfig/d" wscript

  python2 ./waf configure --prefix=/usr \
                          --mandir=/usr/share/man
  python2 ./waf
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  DESTDIR="$pkgdir" python2 ./waf install

  # license
  install -Dm644 COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
