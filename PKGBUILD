# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=cython
pkgver=3.0.10
pkgrel=2
pkgdesc='C-Extensions for Python'
arch=(x86_64)
url='https://cython.org'
license=(Apache-2.0)
depends=(glibc
         python)
replaces=(cython-dev)
makedepends=(python-build
             python-installer
             python-setuptools
             python-wheel)
checkdepends=(gdb
              python-numpy
              python-pytest)
source=(https://github.com/cython/cython/archive/$pkgver/$pkgname-$pkgver.tar.gz)
sha256sums=('00f97476cef9fcd9a89f9d2a49be3b518e1a74b91f377fe08c97fcb44bc0f7d7')

build() {
  cd cython-$pkgver
  python -m build --wheel --no-isolation
}

#check() {
#  cd cython-$pkgver
#  python -m venv --system-site-packages test-env
#  test-env/bin/python -m installer dist/*.whl
#  test-env/bin/python -m pytest -v --ignore docs \
#                                   --ignore pyximport/test/test_reload.py \
#                                   --ignore Cython/Debugger/Tests
#}

package() {
  cd cython-$pkgver
  python -m installer --destdir="$pkgdir" dist/*.whl

  for f in cygdb cython cythonize; do
    mv "$pkgdir"/usr/bin/$f "$pkgdir"/usr/bin/${f}3
    ln -s ${f}3 "$pkgdir"/usr/bin/$f
  done
}
