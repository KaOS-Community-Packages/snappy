pkgname=snappy
pkgver=1.1.3
pkgrel=1
pkgdesc='A fast compressor/decompressor library'
arch=('x86_64')
url="http://google.github.io/snappy/"
license=('BSD')
depends=('glibc' 'gcc-libs')
checkdepends=('zlib')
source=("https://github.com/google/${pkgname}/releases/download/${pkgver}/$pkgname-$pkgver.tar.gz")
sha512sums=('4c4f47c657a072989179be9df0e5e98d14f4a67c27ec7ae0e5a15d14289a75d4e266bc6c5c89723f3e9860408ffcc7138a815f8ad9299407c4a1946fc00ab5bf')

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
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/snappy/LICENSE"
}
