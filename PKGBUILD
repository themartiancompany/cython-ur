# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.25.1
pkgrel=1
pkgdesc="C-Extensions for Python"
arch=(i686 x86_64)
url="http://cython.org"
license=('APACHE')
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://pypi.python.org/packages/2f/ae/0bb6ca970b949d97ca622641532d4a26395322172adaf645149ebef664eb/Cython-$pkgver.tar.gz")
md5sums=('3c1541c15ba511645684a4eaca2cec0f')

package_cython() {
  depends=('python' 'python-setuptools')

  cd "$srcdir"/Cython-$pkgver
  python setup.py install --root="$pkgdir"

  sed -i 's|#!.*python|#!/usr/bin/python3|' "$pkgdir"/usr/bin/*
}

package_cython2() {
  depends=('python2' 'python2-setuptools')

  cd "$srcdir"/Cython-$pkgver
  python2 setup.py install --root="$pkgdir"

  mv "$pkgdir"/usr/bin/cygdb "$pkgdir"/usr/bin/cygdb2
  mv "$pkgdir"/usr/bin/cython "$pkgdir"/usr/bin/cython2
  mv "$pkgdir"/usr/bin/cythonize "$pkgdir"/usr/bin/cythonize2
}
