# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.26
pkgrel=1
pkgdesc="C-Extensions for Python"
arch=(i686 x86_64)
url="http://cython.org"
license=('APACHE')
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://pypi.python.org/packages/10/d5/753d2cb5073a9f4329d1ffed1de30b0458821780af8fdd8ba1ad5adb6f62/Cython-$pkgver.tar.gz")
sha256sums=('4c24e2c22ddaed624d35229dc5db25049e9e225c6f64f3364326836cad8f2c66')

package_cython() {
  depends=('python' 'python-setuptools')

  cd "$srcdir"/Cython-$pkgver
  python setup.py install --root="$pkgdir"

  sed -i 's|#!.*python|#!/usr/bin/python3|' "$pkgdir"/usr/bin/*

  for f in cygdb cython cythonize; do
    mv "$pkgdir"/usr/bin/$f "$pkgdir"/usr/bin/${f}3
    ln -s ${f}3 "$pkgdir"/usr/bin/$f
  done
}

package_cython2() {
  depends=('python2' 'python2-setuptools')

  cd "$srcdir"/Cython-$pkgver
  python2 setup.py install --root="$pkgdir"

  for f in cygdb cython cythonize; do
    mv "$pkgdir"/usr/bin/$f "$pkgdir"/usr/bin/${f}2
  done
}
