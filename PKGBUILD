# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.17
pkgrel=2
pkgdesc='C-Extensions for Python'
arch=(i686 x86_64)
url="http://www.cython.org"
license=('APACHE')
makedepends=('python-distribute' 'python2-distribute')
source=("http://cython.org/release/Cython-$pkgver.tar.gz")
md5sums=('d6b669956b25babf7dd86db0a98539e4')

build() {
  true
}

package_cython() {
  depends=('python')

  cd $srcdir/Cython-$pkgver
  python setup.py install --root=$pkgdir

  sed -i 's|#!.*python|#!/usr/bin/python3|' $pkgdir/usr/bin/*
}

package_cython2() {
  depends=('python2')

  cd $srcdir/Cython-$pkgver
  python2 setup.py install --root=$pkgdir

  mv $pkgdir/usr/bin/cygdb $pkgdir/usr/bin/cygdb2
  mv $pkgdir/usr/bin/cython $pkgdir/usr/bin/cython2
}
