# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=cython
pkgver=3.0.3
pkgrel=2
pkgdesc='C-Extensions for Python'
arch=(x86_64)
url='https://cython.org'
license=(APACHE)
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
source=(https://github.com/cython/cython/archive/$pkgver/$pkgname-$pkgver.tar.gz
        https://github.com/cython/cython/commit/26edfbc0.patch)
sha256sums=('0c2eae8a4ceab7955be1e11a4ddc5dcc3aa06ce22ad594262f1555b9d10667f0'
            'abccff1743c3c79864026b17f19d90b524e6c787647b22b397d197d0b5581446')

prepare() {
  patch -d $pkgname-$pkgver -p1 < 26edfbc0.patch # Fix compilation regressions
}

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
