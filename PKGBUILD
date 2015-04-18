# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.22
pkgrel=3
pkgdesc="C-Extensions for Python "
arch=(i686 x86_64)
url="http://www.cython.org"
license=('APACHE')
makedepends=('python-setuptools' 'python2-setuptools')
source=("http://cython.org/release/Cython-$pkgver.tar.gz"
	https://github.com/cython/cython/commit/9139a7f836151fb5bdb1624a05dce13b1bb17164.patch)
md5sums=('1ae25add4ef7b63ee9b4af697300d6b6'
         '299926d6650d2d8bea960ca0d0cb9c25')

prepare() {
  cd $srcdir/Cython-$pkgver
  patch -p1 <$srcdir/9139a7f836151fb5bdb1624a05dce13b1bb17164.patch
}

package_cython() {
  depends=('python' 'python-setuptools')

  cd $srcdir/Cython-$pkgver
  python setup.py install --root=$pkgdir

  sed -i 's|#!.*python|#!/usr/bin/python3|' $pkgdir/usr/bin/*
}

package_cython2() {
  depends=('python2' 'python2-setuptools')

  cd $srcdir/Cython-$pkgver
  python2 setup.py install --root=$pkgdir

  mv $pkgdir/usr/bin/cygdb $pkgdir/usr/bin/cygdb2
  mv $pkgdir/usr/bin/cython $pkgdir/usr/bin/cython2
  mv $pkgdir/usr/bin/cythonize $pkgdir/usr/bin/cythonize2
}
