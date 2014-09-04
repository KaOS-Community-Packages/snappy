pkgname=snappy
pkgver=1.1.1
pkgrel=1
pkgdesc='A fast compressor/decompressor library'
arch=('x86_64')
url="http://code.google.com/p/snappy/"
license=('BSD')
depends=('glibc' 'gcc-libs')
checkdepends=('zlib')
source=("http://snappy.googlecode.com/files/$pkgname-$pkgver.tar.gz")
md5sums=('8887e3b7253b22a31f5486bca3cbc1c2')

build() {
  cd "$pkgname-$pkgver"

  # compile without assertions
  CXXFLAGS+=\ -DNDEBUG

  ./configure --prefix=/usr
  make
}

check() {
  # compile without assertions
  CXXFLAGS+=\ -DNDEBUG

  make -C "$pkgname-$pkgver" check
}

package() {
  cd "$pkgname-$pkgver"

  make DESTDIR="$pkgdir" install
  install -m644 -D COPYING "$pkgdir/usr/share/licenses/snappy/LICENSE"
}
