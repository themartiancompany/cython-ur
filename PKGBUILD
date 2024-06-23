# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=cython
pkgver=3.0.10
pkgrel=5
pkgdesc='C-Extensions for Python'
arch=(x86_64)
url='https://cython.org'
license=(Apache-2.0)
depends=(glibc
         python)
replaces=(cython-dev)
makedepends=(git
             python-build
             python-installer
             python-setuptools
             python-wheel)
checkdepends=(gdb
              python-numpy
              python-pytest
              python-tests)
source=(git+https://github.com/cython/cython#tag=$pkgver)
sha256sums=('e2cfd1ac69cc31cc3762cf2fa8355228f046748cae7e48622b78f57908b38a64')

build() {
  cd cython
  python -m build --wheel --no-isolation
}

check() {
  cd cython
  python runtests.py -vv -j 64 --no-pyregr
}

package() {
  cd cython
  python -m installer --destdir="$pkgdir" dist/*.whl

  for f in cygdb cython cythonize; do
    mv "$pkgdir"/usr/bin/$f "$pkgdir"/usr/bin/${f}3
    ln -s ${f}3 "$pkgdir"/usr/bin/$f
  done
}
