# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.25.2
pkgrel=1
pkgdesc="C-Extensions for Python"
arch=(i686 x86_64)
url="http://cython.org"
license=('APACHE')
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://pypi.python.org/packages/b7/67/7e2a817f9e9c773ee3995c1e15204f5d01c8da71882016cac10342ef031b/Cython-$pkgver.tar.gz")
sha256sums=('f141d1f9c27a07b5a93f7dc5339472067e2d7140d1c5a9e20112a5665ca60306')

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
