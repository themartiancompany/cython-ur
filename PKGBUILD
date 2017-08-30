# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.26.1
pkgrel=1
pkgdesc="C-Extensions for Python"
arch=(i686 x86_64)
url="http://cython.org"
license=('APACHE')
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://pypi.python.org/packages/68/41/2f259b62306268d9cf0d6434b4e83a2fb1785b34cfce27fdeeca3adffd0e/Cython-$pkgver.tar.gz")
sha256sums=('c2e63c4794161135adafa8aa4a855d6068073f421c83ffacc39369497a189dd5')

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
