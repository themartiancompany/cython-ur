# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.19.2
pkgrel=1
pkgdesc="C-Extensions for Python "
arch=(i686 x86_64)
url="http://www.cython.org"
license=('APACHE')
makedepends=('python-setuptools' 'python2-setuptools')
source=("http://cython.org/release/Cython-$pkgver.tar.gz")
md5sums=('4af1218346510b464c0a6bf15500d0e2')

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
