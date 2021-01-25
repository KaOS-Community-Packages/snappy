pkgname=snappy
pkgver=1.1.8
pkgrel=1
pkgdesc='A fast compressor/decompressor library'
arch=('x86_64')
url="https://github.com/google/snappy"
license=('BSD')
depends=('glibc' 'gcc-libs')
checkdepends=('zlib')
source=("https://github.com/google/snappy/archive/1.1.8.tar.gz")
md5sums=('70e48cba7fecf289153d009791c9977f')

build() {
  cd "$pkgname-$pkgver"
  # compile without assertions
  mkdir -p build
  cd build
  cmake --prefix=/usr ..
  make -j$(nproc)
}

package() {
  cd "$pkgname-$pkgver/build"
  make DESTDIR="$pkgdir" install
}
