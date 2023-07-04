# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=cython
pkgver=0.29.36
pkgrel=1
pkgdesc='C-Extensions for Python'
arch=(x86_64)
url='https://cython.org'
license=(APACHE)
depends=(python)
makedepends=(python-build python-installer python-setuptools python-wheel)
source=(https://github.com/cython/cython/archive/$pkgver/$pkgname-$pkgver.tar.gz)
sha256sums=('bd8ee4208e1f2817914894eca8c4ca894f6c9a51803b0b815a9a3c03d01ab729')

build() {
  cd cython-$pkgver
  python -m build --wheel --no-isolation
}

package() {
  cd cython-$pkgver
  python -m installer --destdir="$pkgdir" dist/*.whl

  for f in cygdb cython cythonize; do
    mv "$pkgdir"/usr/bin/$f "$pkgdir"/usr/bin/${f}3
    ln -s ${f}3 "$pkgdir"/usr/bin/$f
  done
}
